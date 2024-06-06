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
        0: "albumes_ventas_nopcs.png",
        1: "albumes_ventas_pcs.png",
        2: "albumes_ventas_ww_sk.png",
    }

    let chart_tendencia_ventas = "tendencia_ventas_punt_pcs.png"
    let chart_ganancia_ventas = "ganancia_ventas.png"

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

        i=i+1;

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
      <img src="/images/Group 2.png" width="200" alt="pcs_template" />
      <h3 class="headline">
        <b>El nuevo gigante de la industria musical: </b>
        kpop supera en ventas físicas al resto de los géneros
      </h3>
      <p class="bajada">Explorando el efecto del consumismo fan en las ventas de álbumes</p>
      <div class="lorem_ipsum">
        <Loremipsum />
      </div>
    </div>

    <div class="gamification_portion">
        <div class="album_no_pcs">
            <p>Compra tantos álbumes como quieras</p>
            <img src="/images/1989_taylor.png" width=400 alt="ts">
            <button on:click={handleButtonClick}>Comprar</button>
            <div id="contenedor"></div>
        </div>
        <div class="album_pcs">
            <p>Nuevamente, compra tantos álbumes como quieras</p>
            <div class="cero_pcs" style="display:flex; align-items: center; column-gap: 250px">
                <img src="/images/newjeans.png" width=300 alt="nwjns">
                <img id="img_pc" src={pc_colec[i]} width=500 alt="nopcs">
            </div>
            <button on:click={handleButtonClickWithPhotocard}>Comprar</button>
            <div id="contenedor2"></div>
           
        </div>
    </div>


</main>

<style>
    .header {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin-top: 50px;
    margin-bottom: 80px;
  }
  .headline {
    font-size: 30px;
    line-height: 1.2;
    font-weight: normal;
    text-align: center;
    margin: 20px;
  }
  .bajada {
    font-size: 18px;
    font-weight: normal;
    text-align: center;
    margin: 10px;
  }
  .headline b {
    display: block;
  }

  #contenedor {
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

  /* Estilos para el scroller
  .foreground_container {
    pointer-events: none;
    padding-left: 50%;
  } -->

  <!-- .step_foreground {
    display: flex;
    justify-content: end;
    align-items: center;
    height: 100vh;
    border: 1px solid rgba(0, 0, 0, 0.4);
    color: white;
    padding: 1em;
    margin: 0 0 2em 0;
  } -->
  <!-- .epi_foreground {
    padding: 20px;
    max-width: 150px;
    background-color: rgba(0, 0, 0, 0.5);
  } --> */
  .lorem_ipsum {
    margin: 100px auto;
    max-width: 740px;
  }
  .image_container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
</style>
