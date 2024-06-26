<script context="module" lang="ts">
  import {choiceIdKey, type DialogueChoice, genChoiceId} from "../../../model/DialogueChoice";

  function createChoice() {
    return { [choiceIdKey]: genChoiceId() };
  }
</script>
<script lang="ts">
  import {getStateData, getStateKey} from "../DialogueStateView.svelte";
  import EditableTable from "../../../../../lib/EditableTable.svelte";
  import {derived, type Writable} from "svelte/store";
  import McTextInput from "../../../../../lib/McTextInput.svelte";
  import {dialogueStateKeys, dialogueTextFormat} from "../../../dialogueDataStore";
  import {type McText, McTextType} from "../../../../../lib/McText";
  import './dialogue-state-choices.css';
  import {afterUpdate} from "svelte";
  import ChoiceConditionEditor from "./ChoiceConditionEditor.svelte";
  import {StateType} from "../../../model/BlabberDialogue";

  const stateData = getStateData();
  const stateKey = getStateKey();

  const stateChoices: Writable<DialogueChoice[]> = {
    ...derived(stateData, (state) => {
      if (state.type === StateType.ASK_CONFIRMATION) {
        return [
          state?.choices?.[0] ?? createChoice(),
          state?.choices?.[1] ?? createChoice(),
        ]
      }
      return state?.choices ?? [createChoice()];
    }),
    set: (choices: DialogueChoice[]) => stateData.update((oldState) => ({
      ...oldState,
      choices,
    })),
    update: (fn: (oldChoices: DialogueChoice[]) => DialogueChoice[]) => stateData.update((oldState) => ({
      ...oldState,
      choices: fn(oldState.choices ?? []),
    })),
  };

  function stateChoice(index: number) {
    return {
      ...derived(stateChoices, (choices) => choices[index]),
      set: (choice: DialogueChoice) => stateChoices.update((choices) => {
        const newChoices = [...choices];
        newChoices[index] = choice;
        return newChoices;
      }),
      update: (fn: (old: DialogueChoice) => DialogueChoice) => stateChoices.update((choices) => {
        const newChoices = [...choices];
        newChoices[index] = fn(choices[index]);
        return newChoices;
      }),
    };
  }

  let newChoiceId: number | null;

  function appendChoice() {
    newChoiceId = genChoiceId();
    $stateData = {
      ...$stateData,
      choices: [
        ...($stateData.choices ?? []),
        {
          [choiceIdKey]: newChoiceId,
          next: $dialogueStateKeys[0],
        }
      ]
    }
  }

  function updateText(index: number, text: McText) {
    $stateChoices = [
      ...$stateChoices.slice(0, index),
      { ...($stateChoices[index]), text },
      ...$stateChoices.slice(index + 1),
    ];
  }

  function updateNext(index: number, next: string) {
    $stateChoices = [
      ...$stateChoices.slice(0, index),
      { ...($stateChoices[index]), next },
      ...$stateChoices.slice(index + 1),
    ];
  }

  afterUpdate(() => {
    newChoiceId = null;
  });

  function focusNewChoice(node: HTMLElement, choice: DialogueChoice) {
    if (choice[choiceIdKey] === newChoiceId) {
      node.scrollIntoView();
      node.focus();
    }
  }
</script>

<div class="dialogue-choice-editor">
  <h3>
    Available Choices
    {#if $stateData.type !== StateType.ASK_CONFIRMATION}
      <button type="button" class="btn btn-success btn-sm rounded" on:click={appendChoice}>
        New choice
      </button>
    {/if}
  </h3>
  {#if $stateData.type === StateType.ASK_CONFIRMATION}
    <p><em>There can only be 2 (unconditioned) choices for states asking confirmation.</em></p>
  {/if}
  <div class="table-container">
    <EditableTable
      class="table-striped"
      items={stateChoices}
      keyExtractor={(c) => c[choiceIdKey]}
      allowDelete={$stateData.type !== StateType.ASK_CONFIRMATION}
    >
      <svelte:fragment slot="head">
        <th class="col-text">Text</th>
        <th class="col-next">Next State</th>
        {#if $stateData.type !== StateType.ASK_CONFIRMATION}
          <th class="col-advanced">Condition</th>
        {/if}
      </svelte:fragment>
      <svelte:fragment slot="row" let:item let:index>
        <td class="col-text input-cell">
          <McTextInput
            value={item.text}
            inputClass="table-input"
            textFormat={$dialogueTextFormat}
            placeholders={{
              [McTextType.PLAIN]: 'Thank you, ...',
              [McTextType.TRANSLATION_KEY]: `mymod:dialogue.my_dialogue.${$stateKey}.choice_${index}.text`,
              [McTextType.JSON]: '{...}',
            }}
            action={(node) => focusNewChoice(node, item)}
            on:change={(e) => updateText(index, e.detail)}
          />
        </td>
        <td class="col-next input-cell">
          <select class="table-input" on:change={(e) => updateNext(index, e.currentTarget.value)}>
            {#each $dialogueStateKeys as state}
              <option value={state} selected={state === item.next}>{state}</option>
            {/each}
          </select></td>
        {#if $stateData.type !== StateType.ASK_CONFIRMATION}
          <td class="col-advanced input-cell">
            <ChoiceConditionEditor
              stateKey={$stateKey}
              choiceIndex={index}
              choice={stateChoice(index)}
            />
          </td>
        {/if}
      </svelte:fragment>
    </EditableTable>
  </div>
</div>

<style>
  .table-container {
    width: 90%;
    margin: auto;
  }
</style>
