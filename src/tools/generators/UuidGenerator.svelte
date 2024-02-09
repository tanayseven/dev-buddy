<script lang="ts">
  import {v4 as uuidv4} from 'uuid'

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

  const copy = async () => {
    await navigator.clipboard.writeText(uuid)
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
  <input type="number" bind:value={numberOfUuids} on:keyup={refreshUuid}>
  <select bind:value={selectedSeparator} on:change={refreshUuid}>
    {#each Object.entries(separators) as [key, description]}
      <option value={key} selected={selectedSeparator === key}>{description}</option>
    {/each}
  </select>
  <textarea disabled>{uuid}</textarea><br >
  <input type="button" on:click={refreshUuid} value="Refresh">
  <input type="button" on:click={copy} value="Copy">
</div>
