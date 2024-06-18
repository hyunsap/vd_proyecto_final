<script>
    import Scroller from "@sveltejs/svelte-scroller"
    import {onMount} from "svelte"
    import * as d3 from "d3"
    import DebugScroller from "./components/DebugScroller.svelte"
    import Loremipsum from "./components/Loremipsum.svelte"

    /* Variables para el scroller1 */
    let count
    let index
    let offset
    let progress
    let top = 0.1
    let threshold = 0.5
    let bottom = 0.9

    /* Variables para el scroller 2 */
    let count2
    let index2
    let offset2
    let progress2
    let top2 = 0.1
    let threshold2 = 0.5
    let bottom2 = 0.9

    /*Imagen cambiante pcs*/
    let pc_colec = ["images/pcs0.png", "images/pcs1.png", "images/pcs2.png", "images/pcs3.png", "images/pcs4.png", "images/pcs5.png"]
    let i = 0

    /* Charts */
    let charts_ventas = {
        0: "images/albumes_ventas_nopcs.png",
        1: "/images/albumes_ventas_pcs.png",
        2: "/images/albumes_ventas_ww_sk.png",
    }

    let chart_tendencia_ventas = "/images/tendencia_ventas_punt_pcs.png"
    let chart_ganancia_ventas = "/images/ganancia_ventas.png"

    function handleButtonClick() {
        const textoAnimado = document.createElement("div");
        textoAnimado.className = "animated-text";
        textoAnimado.textContent = "-$30";

        const contenedor = document.getElementById("contenedor");
        contenedor.appendChild(textoAnimado);

        // Eliminar el texto animado después de la animación
        setTimeout(() => {
            contenedor.removeChild(textoAnimado);
        }, 1000); // Debe coincidir con la duración de la animación en CSS
    }

    function handleButtonClickWithPhotocard() {
        const textoAnimado = document.createElement("div");
        textoAnimado.className = "animated-text";
        textoAnimado.textContent = "-$30 + 1 photocard";

      

        i=(i+1) % pc_colec.length;

        const contenedor = document.getElementById("contenedor2");
        contenedor.appendChild(textoAnimado);

        // Eliminar el texto animado después de la animación
        setTimeout(() => {
            contenedor.removeChild(textoAnimado);
        }, 1000); // Debe coincidir con la duración de la animación en CSS
    }

    onMount(()=>{})
</script>

<main>
    <div class="header">
      <img src="/images/florcitas.png" width="100%" alt="portada" >
    </div>
    <div class="content">
      <div class="bajada">
        <p>En un contexto mundial de dominancia del streaming respecto a otros formatos de consumo musical, las ventas de discos se encuentran en bajada. Pero, sorprendentemente, hay un segmento de la industria dónde se están observando diferentes resultados. Con su particular <span class="highlight">modelo de ventas</span> y <span class="highlight">diseño de productos</span>, el kpop representa un fenómeno único en la escena musical actual. </p>
      </div>
    

    <div class="gamification_portion">
        <div class="album_no_pcs">
            <p>Para contemplar la diferencia entre la experiencia a nivel comprador entre comprar un álbum proveniente de la industria musical occidental y comprar un álbum de kpop, se propone participar en el siguiente juego. Es meramente una experiencia lúdica, sin ningún tipo de impacto en la realidad.</p>
            <br>
            <p>Tenés la posibilidad de comprar el álbum de Taylor Swift 1989. Compra tantos álbumes como quieras</p>
            <img src="/images/1989_taylor.png" width=350px margin-top=10px alt="ts">
            <br>
            <img src="/images/boton.png" class="botonImagen" alt="boton" on:click={handleButtonClick}>
            <!-- <button on:click={handleButtonClick}>Comprar</button> -->
            <div id="contenedor"></div>
        </div>
        <br>
        <br>
        <div class="album_pcs">
            <p>Ahora, tenés la posibilidad de comprar el álbum de NewJeans Get Up. Nuevamente, compra tantos álbumes como quieras</p>
            <div class="cero_pcs" style="display:flex; align-items: center; column-gap: 250px">
                <img src="/images/newjeans2.png" width=400 alt="nwjns">
                <img id="img_pc" src={pc_colec[i]} width=500 alt="nopcs">
            </div>
            <img src="/images/boton.png" class="botonImagen" alt="boton" on:click={handleButtonClickWithPhotocard}>
            <div id="contenedor2"></div>           
        </div>
    </div>
    <div class="story">
      {#if progress < 1}
      <!-- <DebugScroller
        index={index}
        count={count}
        offset={offset}
        progress={progress}
        /> -->
      {/if}

    <Scroller
      top={top2}
      threshold={threshold2}
      bottom={bottom2}
      bind:count={count2}
      bind:index={index2}
      bind:offset={offset2}
      bind:progress={progress2}
      >
      <div slot="background" class="image_container">
        <img src={charts_ventas[index2]} width="500px" alt="charts_ventas">
      </div>
      <div slot="foreground" class="foreground_container">
        <section class="step_foreground">
          <div class="epi_foreground">
            <h3>¿Cómo se ve el mercado de ventas en música?</h3>
            <p>Las ventas de álbumes occidentales en la última década presentan una baja
              de ventas físicas gradual, en gran parte causada por la aparición de los 
              servicios de streaming.
            </p>
          </div>
        </section>
        <section class="step_foreground">
          <div class="epi_foreground">
            <h3>¿Qué diferencia se encuentra en kpop?</h3>
            <p>Por el contrario, las ventas en kpop cada año aumentan de manera exponencial,
              ya que ofrecen una experiencia de consumidor más personalizada y llamativa.
              Todo el diseño del álbum y sus inclusiones están pensados para la venta masiva.
            </p>
          </div>
        </section>
        <section class="step_foreground">
          <div class="epi_foreground">
            <h3>¿Cómo se afecta al mercado actual?</h3>
            <p>Se ha llegado a un punto en el que la venta de álbumes de kpop ha superado
               a los álbumes del resto de la industria musical, causando una especie de 
               renacimiento del mercado musical físico</p>
          </div>
        </section>
      </div>
    </Scroller>
    <div class="top20">
      <p>En el 2023 ha ocurrido un suceso histórico: 19 de los 20 álbumes mejores vendidos
         forman parte del género musical emergente desde hace ya varios años. 
         Según los registros de la IFPI (Federación Internacional de la Industria Fonográfica), 
         el único álbum cuyas ventas físicas alcanzaron el top es 1989 (Taylor’s Version), 
         lanzado por una de las artistas más populares del momento Taylor Swift. 
      </p>
      <p>Este fenómeno encuentra una posible explicación en una característica muy 
        particular de los álbumes de kpop: las inclusiones. 
        Especialmente, las photocards. Se trata de piezas coleccionables randomizadas, 
        con fotos de artistas, muy codiciadas por los fans.</p>
      <p>Cada álbum comprado contiene generalmente 1 o 2 de estas piezas, 
        y la colección total puede ser muy extensa, llegando a más de 100 
        photocards totales en algunos casos. Por ello, se ha extendido en la 
        comunidad fan del kpop la práctica de comprar álbumes en cantidad con tal de 
        completar una colección de photocards, y luego descartar los discos repetidos. 
      </p>
      <p>Se puede encontrar entonces una correlación muy fuerte entre 
        cantidad de ventas físicas de un álbum y la cantidad total de photocards 
        que pertenecen a la colección de dicho álbum.
      </p>
      <img src={chart_tendencia_ventas} alt="ventasxpcs" width=500/>
    </div>
    </div>
  </div>


</main>

<style>
    .header {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  .content{
    margin:100px;
    margin-bottom:0px;
    font-family: "Lato";
    font-size: 20px;
    color:rgb(105, 103, 103);
  }

  .highlight{
    color: #EACB00;
    font-weight: bold;
  }

  .botonImagen{
    cursor:pointer;
  }
  /* .headline {
    font-size: 30px;
    line-height: 1.2;
    font-weight: normal;
    text-align: center;
    margin: 20px;
  } */
  .bajada {
    font-family: "Lato";
    font-size: 25px;
    font-weight: normal;
    text-align: center;
    color: rgb(105, 103, 103);
    margin-bottom: 100px;
    margin-top: -50px;

  }
  .headline b {
    display: block;
  }

  #contenedor, #contenedor2 {
    position: relative;
    display: inline-block;
}

  .animated-text {
    position: absolute;
    color: red;
    font-size: 40px;
    font-weight: bold;
    animation: fadeOutMoveUp 1s forwards;
  }

@keyframes fadeOutMoveUp {
    0% {
        opacity: 1;
        top: 0;
    }
    100% {
        opacity: 0;
        top: -50px;
    }
}

  /* Estilos para el scroller */
  .foreground_container {
    pointer-events: none;
    padding-left: 50%;
  }

  .step_foreground {
    display: flex;
    justify-content: end;
    align-items: center;
    height: 100vh;
    /* border: 1px solid rgba(0, 0, 0, 0.4); */
    color: white;
    padding: 1em;
    margin: 0 0 2em 0;
  } 
  .epi_foreground {
    padding: 20px;
    max-width: 500px;
    background-color: #738CCC;
    /* border-radius: 20px; */
  }

  .image_container {
    display: flex;
    justify-content: start;
    align-items: center;
    height: 600px;
  }
</style>
