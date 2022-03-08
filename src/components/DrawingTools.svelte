<script>
    import {tool} from '../stores';
    const setTool = (newTool) => $tool.metod = newTool.target.value;  
</script>

<style>
    main
    {
        height: fill;
        max-width: 200px;
        display: flex;
        flex-direction: column;
        background-color: var(--text);
        padding: 8px;
        border-radius: 8px;
    }
    span{
        width: 20px; height: 20px;
        border-radius: 3px;
        display: inline-block;
    }
    div{
        width: 100%;
    }
</style>

<main>
    <div>
        <span style="background: red;" on:click={()=>{$tool.color='red'}}></span>
        <span style="background: blue;" on:click={()=>{$tool.color='blue'}}></span>
        <span style="background: green;" on:click={()=>{$tool.color='green'}}></span>
        <span style="background: orange;" on:click={()=>{$tool.color='orange'}}></span>
        <span style="background: yellow;" on:click={()=>{$tool.color='yellow'}}></span>
    </div>
    <input type="color" name="" id="">
    <div>
        <button on:click={setTool} value="pixel">pixel</button>
        <button on:click={setTool} value="eraser">eraser</button>
        <button on:click={setTool} value="fill">fill</button>
        <button on:click={setTool} value="line">line</button>
    </div>
    {$tool.metod} {$tool.color}
</main>