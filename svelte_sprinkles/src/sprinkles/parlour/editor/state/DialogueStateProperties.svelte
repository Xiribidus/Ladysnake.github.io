<script lang="ts">
  import StateTypeInput from "./type/StateTypeInput.svelte";
  import StateActionInput from "./StateActionInput.svelte";
  import StateTextInput from "./StateTextInput.svelte";
  import {getStateData} from "./DialogueStateView.svelte";
  import {StateType} from "../../model/BlabberDialogue";

  const stateData = getStateData();
</script>
<form id="dialogue-state-properties">
  <StateTypeInput/>
  <StateActionInput/>
  {#if $stateData.type !== StateType.END_DIALOGUE}
    <StateTextInput/>
  {/if}
</form>

<style>
  form {
    margin-top: 1rem;
    margin-bottom: 1rem;
    display: grid;
    grid-template-columns: min-content auto;
    grid-auto-rows: minmax(3.1rem, max-content);
    column-gap: 1rem;
    row-gap: 0.5rem;
    background-color: var(--button-background);
    padding: 1rem;
    align-items: center;
  }

  form :global(input) {
    background-color: transparent;
    border: 1px solid var(--button-outline);
    padding: 0.5rem;

    &:invalid {
      border-color: var(--color-invalid);
      color: var(--color-invalid);
    }
  }
</style>
