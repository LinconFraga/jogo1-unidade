<script lang="ts">
    let tituloDoJogo : string = "Zatmenia"
</script>
<style>
    @font-face {
        font-family: 'OldLondon';
        src: url('/src/assets/fontes/OldLondon.ttf');
        font-weight: normal;
        font-style: normal;
    }
    #titulo {
        font-family: 'OldLondon';
        font-size: 112px;
        margin: 5%;
        color: rgb(243, 227, 206);
        text-shadow: 3px 3px 5px #ee2424;
    }

        @font-face {
        font-family: 'Bronco';
        src: url('/src/assets/fontes/BroncoPersonalUse.ttf');
        font-weight: normal;
        font-style: normal;
    }
    .menu{
        font-family: "Bronco";
    }
</style>

    <h1 id="titulo">
        {tituloDoJogo}
    </h1>
    
    <br />
    <a class="menu" href="/jogar">Jogar</a>
    <br />
    <a class="menu" href="/sobre">Sobre</a>
