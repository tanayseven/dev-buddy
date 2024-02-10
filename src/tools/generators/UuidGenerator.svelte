<script lang="ts">
  import {v4 as uuidv4} from 'uuid'
  import CopyButton from "../../components/CopyButton.svelte"
  import MonacoEditor from "../../components/MonacoEditor.svelte"

  let numberOfUuids = 1
  let selectedSeparator = ","

  let uuid = ""

  const generateUuids = (total: number): string => {
    let uuids = []
    for (let i = 0; i < total; i++) {
      uuids.push(uuidv4())
    }
    return uuids.join(selectedSeparator)
  }

  const refreshUuid = () => {
    uuid = generateUuids(numberOfUuids)
  }

  const separators = {
    ",": "',' Comma separated",
    "\n": "'\\n' New line separated",
    "\t": "'\\t' Tab separated",
    " ": "' ' Space separated",
  }

  uuid = generateUuids(numberOfUuids)
</script>

<div>
  <input type="number" bind:value={numberOfUuids} on:keyup={refreshUuid} on:change={refreshUuid}>
  <select bind:value={selectedSeparator} on:change={refreshUuid}>
    {#each Object.entries(separators) as [key, description]}
      <option value={key} selected={selectedSeparator === key}>{description}</option>
    {/each}
  </select>
  <MonacoEditor bind:content={uuid} language="plaintext" readOnly />
  <input type="button" on:click={refreshUuid} value="Refresh">
  <CopyButton bind:text={uuid} />
</div>
