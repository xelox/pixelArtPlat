<script>
    import PXHeader from '../components/PXHeader.svelte';

</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Ubuntu:ital,wght@0,300;0,400;0,500;0,700;1,300;1,400;1,500;1,700&family=Zen+Kaku+Gothic+Antique&display=swap');

    :root{
        --wash: #222831;
        --base: #393E46;
        --middle: #C6DE41;
        --detail: #FFD369;
        --text: #dfdfdf;
        --blue_label: rgba(73, 124, 153, 0.5);
        --blue_detail: #95c4eb;

        --pastel_green: #8cd673;
        --pastel_yello: #d6bd73;
        --pastel_red: #d68f73;
        --gray: rgb(160, 160, 160);

        --small: 14px;
        --normal: 18px;
    } 
    
    body
    {
        background-color: var(--wash);
        width: 100%;
        margin: 0; padding: 0; box-sizing: none;
    }
    *{
        font-family: "ＭＳ Ｐゴシック";
        -webkit-font-smoothing: none;
        font-weight: bolder;
    }
    
</style>

<body>     
    <PXHeader />
    <slot/>
</body>

