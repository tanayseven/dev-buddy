<script lang="ts">
    export let text: string
    const copy = async () => {
        await navigator.clipboard.writeText(text)
    }
</script>

<button on:click={copy}>Copy</button>
