<script context="module" lang="ts">
  function shiftElementBackward<E>(arr: E[], index: number) {
    if (index <= 0) throw Error('Cannot shift backward the first element of an array');
    const ret = [...arr];
    ret[index] = arr[index - 1];
    ret[index - 1] = arr[index];
    return ret;
  }
  function shiftElementForward<E>(arr: E[], index: number) {
    if ((index + 1) >= arr.length) throw Error('Cannot shift forward the last element of an array');
    const ret = [...arr];
    ret[index] = arr[index + 1];
    ret[index + 1] = arr[index];
    return ret;
  }

  function deleteElement<E>(arr: E[], index: number) {
    if (index < 0 || index >= arr.length) throw Error('Invalid index ' + index + ' for array ' + JSON.stringify(arr));
    const ret = [...arr];
    ret.splice(index, 1);
    return ret;
  }

  export type KeyExtractor<T> = (item: T, index: number) => unknown;
</script>
<script lang="ts" generics="T">
  import type {Writable} from "svelte/store";
  import {afterUpdate, beforeUpdate} from "svelte";

  let className: string = '';
  // noinspection ReservedWordAsName
  export { className as class };
  export let items: Writable<T[]>;
  export let keyExtractor: KeyExtractor<T>;
  export let allowDelete = true;

  function moveUp(index: number) {
    $items = shiftElementBackward($items, index);
  }

  function moveDown(index: number) {
    $items = shiftElementForward($items, index);
  }

  function deleteRow(index: number) {
    $items = deleteElement($items, index);
  }

  let table: HTMLTableElement;

  // Ensures focus is preserved when swapping table rows
  let activeElement: HTMLElement | null;

  beforeUpdate(() => {
    activeElement = document.activeElement as HTMLElement | null;
  });

  afterUpdate(() => {
    if (activeElement && table.contains(activeElement)) {
      if ((activeElement as any).disabled) {
        if (activeElement.classList.contains('sort-up')) {
          (activeElement.parentElement?.querySelector('.sort-down') as HTMLElement)?.focus();
        } else if (activeElement.classList.contains('sort-down')) {
          (activeElement.parentElement?.querySelector('.sort-up') as HTMLElement)?.focus();
        }
      } else {
        activeElement.focus();
      }
    }
    activeElement = null;
  });
</script>
<div class="table-editable">
  <table bind:this={table} class={className}>
    <thead>
    <tr>
      <slot name="head"/>
      <th class="col-sort">Sort</th>
      {#if allowDelete}
      <th class="col-remove">Remove</th>
      {/if}
    </tr>
    </thead>
    <tbody>
    {#each $items as item, index (keyExtractor?.(item, index) ?? index)}
      <tr>
        <slot name="row" item={item} index={index}/>
        <td class="col-sort">
          <button class="table-input sort-up" disabled={index === 0} on:click={() => moveUp(index)}><svg inline-src="octicon-arrow-up"/></button>
          <button class="table-input sort-down" disabled={index + 1 >= $items.length} on:click={() => moveDown(index)}><svg inline-src="octicon-arrow-down"/></button>
        </td>
        {#if allowDelete}
        <td class="col-remove">
            <button class="table-input" type="button" on:click={() => deleteRow(index)}>
            <svg inline-src="octicon-x"/>
          </button>
        </td>
        {/if}
      </tr>
    {/each}
    </tbody>
  </table>
</div>
<style>
  table {
    width: 100%;
  }
</style>
