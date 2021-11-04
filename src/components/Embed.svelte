<script>
    export let url;
    export let timeout;

    function refresh() {
        document.getElementById("iframe").src += "";
    }

    setInterval(refresh, timeout * 1000);
</script>

<div>
    <iframe title="" id="iframe" src={url}></iframe>
</div>

<style>
    #iframe {
        height: 100vh;
        width: 100vw;
        border: none;
        padding: 0;
        margin: 0;
    }
</style>
