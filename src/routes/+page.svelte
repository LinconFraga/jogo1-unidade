<script lang="ts">
    let tituloDoJogo : string = "Zatmenia"
</script>
<style>
    #titulo {
        font-family: 'OldLondon';
        font-size: 112px;
        margin: 5%;
        color: rgb(243, 227, 206);
        text-shadow: 3px 3px 5px #ee2424;
    }
    .inicio {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
</style>

    <h1 id="titulo">
        {tituloDoJogo}
    </h1>
    <div class="inicio">
        <a class="menu" href="/jogar">Jogar</a>
        <a class="menu" href="/sobre">Sobre</a>
    </div>
    