<script lang=ts>
import { onMount } from "svelte";
import {tool} from '../stores';

    let canvas:HTMLCanvasElement;
    let ctx:CanvasRenderingContext2D;
    let mouseIsDown:boolean = false;
    let mouseCoords:{x:number, y:number} = {x:0, y:0}; 
    let pixelRatio:number;
    let roundedCoords:{x:number, y:number} = {x:0, y:0};
    let canvasSize:number;

    onMount(async () => 
    {
        canvas.width = 64;
        canvas.height = 64;
        pixelRatio = canvasSize / 64;
        ctx = canvas.getContext('2d');
        
    });

    const mousedown:{():void} = () => { mouseIsDown = true; drawPixel(); }
    const mouseup:{():void} = () => mouseIsDown = false;
    const mousemove:{(event:MouseEvent):void} = (ev:MouseEvent) =>
    {
        var rect = canvas.getBoundingClientRect();
        mouseCoords.x = ev.clientX - rect.left;
        mouseCoords.y = ev.clientY - rect.top;
        
        if(mouseIsDown) drawPixel();
    }

    const drawPixel = () => {
        pixelRatio = canvasSize / 64;
        roundedCoords.x = Math.floor((mouseCoords.x - 1) / pixelRatio);
        roundedCoords.y = Math.floor((mouseCoords.y - 1) / pixelRatio);
        
        ctx.beginPath();
        ctx.fillStyle = $tool.color;
        ctx.fillRect(roundedCoords.x, roundedCoords.y, 1, 1);
        ctx.fill();
    }

</script>


<style>
    canvas{
        background-color: white;

        border-radius: 8px;
        aspect-ratio: 1/1;
        width: 100%;

        image-rendering: optimizeSpeed;             /* Older versions of FF          */
        image-rendering: -moz-crisp-edges;          /* FF 6.0+                       */
        image-rendering: -webkit-optimize-contrast; /* Safari                        */
        image-rendering: -o-crisp-edges;            /* OS X & Windows Opera (12.02+) */
        image-rendering: pixelated;                 /* Awesome future-browsers       */
        -ms-interpolation-mode: nearest-neighbor;   /* IE                            */
    }
</style>


<canvas bind:this={canvas} on:mousedown={mousedown} on:mouseup={mouseup} on:mousemove={mousemove} bind:clientWidth={canvasSize}>

</canvas>