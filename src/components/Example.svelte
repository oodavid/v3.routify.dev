<script>
    import { Details, SmoothBox } from 'polykit'
    import { resolveNode, node } from '@roxi/routify'
    import FilesViewer from '#cmp/FilesViewer.svelte'
    import Browser from '#cmp/minibrowser/MiniBrowser.svelte'
    export let path
    export let title
    export let focus = null
    export let show = false
</script>

<div class="example">
        <Details {show}>
            <button class="button-outline" slot="activator">Show example</button>
            <span class="close" slot="deactivator">✖</span>
            <div class="">
                <h4>{title}</h4>
                <div class="left-bar" />
                <div class="fv">
                    <FilesViewer root={resolveNode(path)} {focus} />
                </div>
                <div class="ex">
                    <Browser rootNode={$node.traverse(path)} slot="browser" />
                </div>
            </div>
        </Details>
</div>

<style>
    .close {
        position: absolute;
        top: 8px;
        right: 8px;
    }
    .example {
        position: relative;
        margin-bottom: 96px;
    }
    .left-bar {
        position: absolute;
        width: 16px;
        top: 16px;
        bottom: -16px;
        left: -40px;

        border-left: 4px solid var(--color-grey-300);
        border-top: 4px solid var(--color-grey-300);
        border-bottom: 4px solid var(--color-grey-300);
        border-bottom-left-radius: 16px;
        border-top-left-radius: 16px;
    }
    h4 {
        margin: 40px 0 16px;
        padding-bottom: 1rem;
        font-weight: bold;
    }
    .fv {
        padding-bottom: 32px;
    }
</style>
