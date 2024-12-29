<script lang="ts">
    import { goto } from '$app/navigation'    
    
    // tipo para guardar as coordenadas do personagem e do objetivo
    class Coordenada {
        linha : number
    }

    // representa estado do jogo, contendo o mapa e a locação do personagem e do objetivo 
    class EstadoJogo {
        posicaoPersonagem : Coordenada
        posicaoObjetivo : Coordenada
        mapa : number[][]
    }

    // cria o estado do jogo
    function inicializarJogo() : EstadoJogo {
        let personagem : Coordenada = new Coordenada()
        personagem.linha = 0

        let objetivo : Coordenada = new Coordenada()
        objetivo.linha = 9

        let mapa : number[] = [0, 0, 0, 0, 0, 0, 0, 0, 1, 0]
                        

        let estado : EstadoJogo = new EstadoJogo()
        estado.posicaoPersonagem = personagem
        estado.posicaoObjetivo = objetivo
        estado.mapa = mapa

        return estado;
        
    }

    // detecta quando o personagem faz um movimento inválido 
    function houveColisao(posicao : Coordenada, jogo : EstadoJogo) : boolean {
        return (posicao.linha < 0) || (posicao.linha >= jogo.mapa.length)
            || jogo.mapa[posicao.linha] == 1
    }

    // trata o evento de perssionar as setas no teclado
 	function onKeyDown(evento) : void {
        let novaPosicao = new Coordenada()
        novaPosicao.linha = jogo.posicaoPersonagem.linha

		 switch(evento.keyCode) {
			 case 37: // left
                novaPosicao.linha--
				break;
			 case 39: // right
                novaPosicao.linha++
				break;       
		 }
         if(houveColisao(novaPosicao, jogo)){ //acrescenta um dialogo ao haver colisão
            alert("quer um cafezim?")
         }
        
        if (novaPosicao.linha == jogo.posicaoObjetivo.linha) {
            alert("Parabéns, você chegou ao objetivo")
            goto("/")
        }

        if(!houveColisao(novaPosicao, jogo)) {
            jogo.posicaoPersonagem = novaPosicao
        }
	}

    // cria o objeto contendo o estado do jogo
    let jogo : EstadoJogo = inicializarJogo()
    
</script>

<h1>Movimente o personagem (quadrado cinza) até o objetivo (quadrado roxo)</h1>

<table>
<tr>  
    {#each jogo.mapa as linha, i}
                {#if i == jogo.posicaoPersonagem.linha}
                    <td class="celula personagem"></td>
                {:else if i == jogo.posicaoObjetivo.linha}
                    <td class="celula objetivo"></td>
                {:else if jogo.mapa[i] == 0}
                    <td class="celula"></td>
                {:else}
                    <td class="celula bloco"></td>
                {/if}
    {/each}  
</tr>  
</table>

<br />

<a class="menu" href="/">Voltar ao Menu</a>

<svelte:window on:keydown|preventDefault={onKeyDown} />