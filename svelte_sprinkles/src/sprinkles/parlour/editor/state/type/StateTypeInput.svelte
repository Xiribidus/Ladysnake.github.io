<script lang="ts">
  import ConfirmDialogueLayout from "./ConfirmDialogueLayout.svelte";
  import EndDialogueLayout from "./EndDialogueLayout.svelte";
  import DefaultDialogueLayout from "./DefaultDialogueLayout.svelte";
  import {getStateData} from "../DialogueStateView.svelte";
  import {StateType} from "../../../model/BlabberDialogue";

  const stateData = getStateData();

  $: value = $stateData.type ?? 'default';

  function onChange(event: Event & { currentTarget: HTMLInputElement }) {
    $stateData = {
      ...$stateData,
      type: event.currentTarget.value as StateType,
    };
  }
</script>

<fieldset>
  <legend>Type</legend>
  <input
    type="radio"
    autocomplete="off"
    class="layout-selection"
    value={StateType.DEFAULT}
    id="dialogue-state-default-type"
    name="dialogue-state-type"
    bind:group={value}
    on:change={onChange}
  >
  <label for="dialogue-state-default-type">
    <span>Default</span>
    <DefaultDialogueLayout/>
  </label>
  <input
    type="radio"
    autocomplete="off"
    class="layout-selection"
    value={StateType.ASK_CONFIRMATION}
    id="dialogue-state-confirm-type"
    name="dialogue-state-type"
    bind:group={value}
    on:change={onChange}
  >
  <label for="dialogue-state-confirm-type">
    <span>Confirm</span>
    <ConfirmDialogueLayout/>
  </label>
  <input
    type="radio"
    autocomplete="off"
    class="layout-selection"
    value={StateType.END_DIALOGUE}
    id="dialogue-state-ending-type"
    name="dialogue-state-type"
    bind:group={value}
    on:change={onChange}
  >
  <label for="dialogue-state-ending-type">
    <span>Ending</span>
    <EndDialogueLayout/>
  </label>
</fieldset>

<style>
  fieldset {
    grid-column-end: span 2;
  }

  .layout-selection {
    opacity: 0;
    width: 0;

    & + label {
      display: inline-flex;
      flex-direction: column;
      max-width: 30%;
      margin-right: 1rem;
      margin-left: 0.5rem;
      border: 2px solid var(--button-outline);
      background-color: var(--base-background-color);

      & span {
        text-align: center;
        border-bottom: 2px solid var(--button-outline);
        background-color: var(--button-background);
      }
    }

    &:checked + label {
      border-color: var(--button-selected-outline);

      & span {
        border-color: var(--button-selected-outline);
        background-color: var(--button-selected-outline);
      }
    }
  }
</style>
