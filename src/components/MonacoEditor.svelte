<script lang="ts">
    import { onMount, onDestroy } from "svelte"
    import type * as Monaco from 'monaco-editor/esm/vs/editor/editor.api'
    let editor: Monaco.editor.IStandaloneCodeEditor
    let monaco: typeof Monaco
    let editorContainer: HTMLElement
    export let content: string
    export let language: string

    export let readOnly: boolean = false

    let model: Monaco.editor.ITextModel

    onMount(async () => {
        // Import our 'monaco.ts' file here
        // (onMount() will only be executed in the browser, which is what we want)
        monaco = (await import('../lib/monaco')).default

        // Your monaco instance is ready, let's display some code!
        editor = monaco.editor.create(
            editorContainer,
            {readOnly}
        );
        model = monaco.editor.createModel(
            content,
            language
        );
        editor.setModel(model);
    });

    $: if (model) {
        model.setValue(content)
    }

    $: if (monaco && editor) {
        monaco.editor.setModelLanguage(model, language)
    }

    $: if (editor) {
        editor.updateOptions({ readOnly })
    }

    onDestroy(() => {
        monaco?.editor.getModels().forEach((model) => model.dispose());
        editor?.dispose();
    });
</script>

<div class="monaco-editor" bind:this={editorContainer} />