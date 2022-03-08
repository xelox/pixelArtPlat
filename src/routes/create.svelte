
<script lang='ts'>
    import DrawingTools from "../components/DrawingTools.svelte"; 
    import PXCanvas from "../components/PXCanvas.svelte";
    import { fade } from 'svelte/transition';
    import {tool} from '../stores';
</script>

<style>
    h1{
        text-align: center;
        color: var(--text);
    }
    div{
        position: relative;
        width: 70%;
        min-height: calc(100vh - 200px);
        left: 50%; transform: translateX(-50%);
        align-items: center;
        justify-content: center;
        display: flex;
    }

</style>



<main transition:fade>
    <h1>Create - {$tool.metod}</h1>
    <div>
        <span style="display:block; width: 100%; margin: 0 10px 0 0; display: flex; align-items: center; justify-content: center;">
            <PXCanvas />
        </span>
        <DrawingTools />
    </div>
</main>