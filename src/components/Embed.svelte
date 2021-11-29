<script>
    export let url;
    export let timeout = 0;
    export let zoom = 100;

    function refresh() {
        document.getElementById("iframe").src += "";
    }

    if (timeout > 0) setInterval(refresh, timeout * 1000);

    const zoomStyle = `zoom: ${zoom/100.00};
        -moz-transform: scale(${zoom/100.00});
        -moz-transform-origin: 0 0;
        -o-transform: scale(${zoom/100.00});
        -o-transform-origin: 0 0;
        -webkit-transform: scale(${zoom/100.00});
        -webkit-transform-origin: 0 0;
        height: calc(1 / ${zoom/100.00} * 100%);
        width: calc(1 / ${zoom/100.00} * 100%);`;
</script>

<div class="wrap">
    <iframe title="" id="iframe" src={url} style={zoomStyle}></iframe>
</div>

<style>
    .wrap {
        height: 100%;
        width: 100%;
        overflow: hidden;
    }
    #iframe {
        height: 100%;
        width: 100%;
        border: none;
        padding: 0;
        margin: 0;
    }
</style>
