<script>
    import Scroller from "@sveltejs/svelte-scroller"
    import {onMount} from "svelte"
    import * as d3 from "d3"
    import DebugScroller from "./components/DebugScroller.svelte"
    // import Chart from "./components/charts.svelte"
    // import Charts from "./components/charts.svelte";

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
    let threshold2 = 0.1
    let bottom2 = 0.1
    
    /*Imagen cambiante pcs*/
    let pc_colec = ["images/pcs/pcs0.png", "images/pcs/pcs1.png", "images/pcs/pcs2.png", "images/pcs/pcs3.png", "images/pcs/pcs4.png", "images/pcs/pcs5.png"]
    let i = 0

    /* Charts */
    let charts_ventas = {
        0: "images/falopeada2.png",
        1: "/images/falopeada1.png",
        2: "/images/falopeada3.png",
        3: "/images/falopeada4.png"
    }

    let charts_ventas2 = {
        0: "images/falopeada2_2.png",
        1: "/images/falopeada1_2.png",
        2: "/images/falopeada3.png",
        3: "/images/falopeada4_2.png"

    }

    let chart_top0 = {0: "/images/prim.png", 1: "/images/segun.png",2:"/images/ter.png",3:"/images/cuar.png",
      4:"/images/quinto.png", 5:"/images/sext.png",6:"/images/sept.png",7:"/images/oct.png",8:"/images/nov.png",
      9:"/images/dec.png",10:"/images/once.png",11:"/images/doce.png",12:"/images/trece.png",13:"/images/cator.png",
      14:"/images/quince.png",15:"/images/dcseis.png",16:"/images/dcsiet.png",17:"/images/dcocho.png",18:"/images/dcnuev.png",
      19:"/images/veinte.png",20:"/images/vntuno.png",}
    let chart_top = {0: "/images/prim2.png",1:"/images/segun2.png",2:"/images/ter2.png",3:"/images/cuar2.png",
      4:"/images/quinto2.png", 5:"/images/sext2.png",6:"/images/sept2.png",7:"/images/oct2.png",8:"/images/nov2.png",
      9:"/images/dec2.png",10:"/images/once2.png",11:"/images/doce2.png",12:"/images/trece2.png",13:"/images/cator2.png",
      14:"/images/quince2.png",15:"/images/dcseis2.png",16:"/images/dcsiet2.png",17:"/images/dcocho2.png",
      18:"/images/dcnuev2.png",19:"/images/veinte2.png",20:"/images/vntuno2.png"}

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
      <img src="/images/Portada.png" width="100%" alt="portada" >
      <img src="/images/noeasy-cd.png" id='cd' alt="cd">
    </div>

    <div class="content">
      <div class="d1">
        <div class="bajada">
          <p>Para entender lo que esta sucediendo hoy en día con la venta de álbumes físicos, es importante fijarse en como son estos. </p>
        </div>
        <div class="imp-amarillo"><h3>EXPLOREMOS LA EXPERIENCIA ACTUAL DE COMPRAR UN ALBUM</h3></div>
        <img src="/images/botones/flechas.svg" class="up-down" width=30px alt="flechas">
      </div>

    <div class="gamification_portion">
        <div class="album_no_pcs">
          <div class="container"><div class="juego" style="background-color: #1a1a1a; width: 800px"><h3 style="font-family: Anybody; font-weight: bold;text-align: center; color: #02D56D">EXPLOREMOS LA EXPERIENCIA ACTUAL DE COMPRAR UN ÁLBUM</h3></div></div>
            <br>
            <div class="container"><div class="juego" style="background-color: #1a1a1a; width: 570px"><h3 style="font-family: Anybody;font-size: 18px; text-align: center; color: #ffffff">Tenés disponibles estas fichas, canjealas por tantos álbumes como quieras</h3></div></div>
            <br>
            <div class="ficha" style="display:flex; justify-content: center">
              <img src="images/botones/fichas.png" width=80px alt="ficha"></div>
            <p>Tenés la posibilidad de comprar el álbum de Taylor Swift "1989 (Taylor's Version)". Compra tantos álbumes como quieras</p>
            <img src="/images/albums/1989_taylor.png" width=350px margin-top=10px alt="ts">
            <br>
            <img src="/images/boton_compra.png" class="botonImagen" alt="boton" on:click={handleButtonClick}>
            <!-- <button on:click={handleButtonClick}>Comprar</button> -->
            <br>
            <div class="container"><div class="juego" style="background-color: #1a1a1a; width: 570px"><h3 style="font-family: Anybody;font-size: 18px; text-align: center; color: #02D56D">Cuando termines, scrollea a la siguiente sección</h3></div></div>
            <div id="contenedor"></div>
        </div>
        <br>
        <br>
        <div class="album_pcs">
          <div class="container"><div class="juego" style="background-color: #1a1a1a; width: 700px"><h3 style="font-family: Anybody;font-size: 18px; text-align: center; color: #ffffff">En caso de que te hayas gastado todas las fichas, se te reinician</h3></div></div>
          <div class="container"><div class="juego" style="margin-top: 50px;background-color: #1a1a1a; width: 700px"><h3 style="font-family: Anybody;font-size: 18px; text-align: center; color: #ffffff">Ahora el álbum es de kpop. Nuevamente, comprá cuantos quieras</h3></div></div>

            <p>Tenés la posibilidad de comprar el álbum de NCT "Sticker". Compra tantos álbumes como quieras</p>
            <div class="cero_pcs" style="display:flex; align-items: center; column-gap: 250px">
                <img src="/images/albums/sticker.png" width=400 alt="nct">
                <img id="img_pc" src={pc_colec[i]} width=500 alt="nopcs">
            </div>
            <img src="/images/boton_compra.png" class="botonImagen" alt="boton" on:click={handleButtonClickWithPhotocard}>
            <div id="contenedor2"></div>           
        </div>
    </div>

    <br><br>

    <div class="story">
      <div class="container"><div class="pregunta2" style="display:flex; background-color: #1c10f6; height:80px; align-items:center">
        <h3 class="lol" style="color: white; font-family: Anybody">Y esto... ¿De qué sirve? ¿Para qué querría yo fotos de otra gente?</h3>
      </div></div>

      <Scroller
        top={top}
        threshold={threshold}
        bottom={bottom}
        bind:count={count}
        bind:index={index}
        bind:offset={offset}
        bind:progress={progress}
      >
        <div slot="background" class="image_container">
          <!-- <div width="500px"><Chart1 /></div> -->
          <img src={charts_ventas2[index]} alt="charts_ventas">
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
                a los álbumes del resto de la industria musical.</p>
            </div>
          </section>
          <section class="step_foreground">
            <div class="epi_foreground">
              <h3>¿Cómo se afecta al mercado actual?</h3>
              <p>De hecho, a partir de 2020 el mercado físico de álbumes experimenta una repuntada notable, 
                en gran parte motivada por los álbumes de kpop.</p>
            </div>
          </section>
        </div>
      </Scroller>
    </div>
    <br><br>
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
    </div>
    <br>
      <div class="container">
        <div class="pregunta" style="height:80px; align-items:center">
          <h3 class="lol">Top 20: álbumes más vendidos de 2023</h3>
        </div>
      </div>
      <br>

      <div>A partir de la lista de IFPI de los discos con mayores ventas físicas de 2023, se analiza el puntaje de un album, 
        determinado a partir de las ventas físicas totales sobre la popularidad del álbum, y su correlación con la cantidad 
        de photocards presentes, en particular cuántos álbumes habría que comprar para completar la colección si no hubiera repeticiones.</div>
  
    <br><br>
    <!-- Segundo scroller -->
    <Scroller
    top={top2}
    threshold={threshold2}
    bottom={bottom2}
    bind:count={count2}
    bind:index={index2}
    bind:offset={offset2}
    bind:progress={progress2}
  >
  <div slot="background">
    <img src={chart_top[index2]} alt="dad" width=680px>
  </div>
  <div slot="foreground" class="foreground_container2">
    <section class="step_foreground"><div class="epi_foreground">El disco físico más vendido de 2023: FML, de Seventeen. Cuenta con un total de 72 photocards, y cada álbum trae incluidas 2. Cuenta con una puntuación de 18, al tener 6.4 millones de copias vendidas sobre 360 millones de streams.</div></section>
    <section class="step_foreground"><div class="epi_foreground">5-Star de Stray Kids cuenta con el segundo puesto. Con 5.3 millones de copias vendidas sobre 596 millones de streams, su puntuación es de 9 puntos.</div></section>
    <section class="step_foreground"><div class="epi_foreground">En el tercer puesto se encuentra ISTJ de NCT Dream, el cual logró 4.5 millones de ventas.</div></section>
    <section class="step_foreground"><div class="epi_foreground">Seventeen, con un segundo álbum, llega al cuarto lugar con 4.5 millones de ventas, con tan solo 119 millones de streams.</div></section>
    <section class="step_foreground"><div class="epi_foreground">Stray Kids también vuelve a aparecer con Rockstar, álbum que contó con 4.2 millones de copias vendidas y 313 millones de streams.</div></section>
    <section class="step_foreground"><div class="epi_foreground">El único álbum no perteneciente al kpop que se encuentra entre los 20 más vendidos: 1989 (Taylor's Version) de Taylor Swift. Siendo uno de los discos más populares de 2023, con 3 billones de reproducciones, se mete en el top con una puntuación relativamente baja.</div></section>
    <section class="step_foreground"><div class="epi_foreground">Golden de Jungkook, perteneciente a BTS, también cuenta con un alto número de streams que ronda los 3 billones, y solamente un total de 4 photocards, con 2 en cada álbum. Se encuentra en el séptimo lugar con 2.7 millones de copias vendidas.</div></section>
    <section class="step_foreground"><div class="epi_foreground">El octavo puesto pertenece a Exist de EXO, el cual contó con 2.3 millones de ventas y 134 millones de reproducciones. Contiene en total 24 photocards, y cada álbum solo trae 1 incluida.</div></section>
    <section class="step_foreground"><div class="epi_foreground">El noveno puesto pertenece a I've Mine de IVE, el cual contó con 2.2 millones de ventas y 187 millones de reproducciones. Contiene en total 12 photocards, y cada álbum solo trae 1 incluida.</div></section>
    <section class="step_foreground"><div class="epi_foreground">El déximo puesto pertenece a Layover de V, miembro de BTS, que con 1.3 billones de streams y 5 photocards de 15 incluidas alcanzó los 2.2 millones de ventas</div></section>
    <section class="step_foreground"><div class="epi_foreground">En el puesto once se encuentra Youth in the Shade, el álbum debut de Zerobaseone, el cual contó con 2.1 millones de ventas. Impresionante número comparado con las 87 millones de reproducciones que obtuvo el álbum. La versión física incluye 1 photocard de 36.</div></section>
    <section class="step_foreground"><div class="epi_foreground">El doceavo lugar pertenece a NewJeans, con el álbum Get Up, el cual casi alcanzó el billón de reproducciones y contó con 2.1 millones de ventas, conteniendo 5 photocards de 30 en cada disco.</div></section>
    <section class="step_foreground"><div class="epi_foreground">En décimotercer puesto se encuentra aespa, cuyo álbum My World cónto con 239 millones de streams y 2.1 millones de ventas, con 1 photocard incluida de 8 totales. </div></section>
    <section class="step_foreground"><div class="epi_foreground">El puesto catorce pertenece a TXT, con 2 millones de copias vendidas y 268 millones de streams, contando cada disco con 1 photocard de 15.</div></section>
    <section class="step_foreground"><div class="epi_foreground">En el lugar 15, con 2 millones de ventas, se encuentra I Feel de (G)I-dle, el cual contó con 339 millones de streams y 1 photocard de 15 incluida</div></section>
    <section class="step_foreground"><div class="epi_foreground">En el puesto 16 se encuentra Fact Check de NCT 127 con 1.9 millones de copias vendidas y 88 millones de streams. Cuenta con 1 photocard de 27 incluida. </div></section>
    <section class="step_foreground"><div class="epi_foreground">El lugar 17 pertenece a Enhypen con Dark Blood, álbum muy popular con 400 millones de streams y 1.7 millones de ventas. Contiene 1 pc de 27. </div></section>
    <section class="step_foreground"><div class="epi_foreground">Otro álbum de IVE, I've IVE, se encuentra en el puesto 18, con 1.7 millones de ventas y 479 millones de streams. Cuenta con 1 pc incluida de 18.</div></section>
    <section class="step_foreground"><div class="epi_foreground">Otro miembro de BTS, Jimin, aparece en la lista en el penúltimo lugar con el álbum Face, con 1.7 millones de ventas frente a 1.8 billones de streams, contando con un puntaje bastante bajo. Trae 1 pc de 6 posibles.</div></section>
    <section class="step_foreground"><div class="epi_foreground">Por último, nuevamente aparece Enhypen en la lista. Su disco Orange Blood cuenta con 1.7 millones de ventas y 147 millones de reproducciones. Cada álbum incluye 2 photocards de 28 totales.</div></section>
    <section class="step_foreground"><div class="epi_foreground">Se presencia una tendencia de aumento de la puntuación mientras más discos comprados requiera conseguir todas las photocards.</div></section>
  </div>
  </Scroller>

  <div class="corr"><p>Se puede encontrar entonces una correlación bastante fuerte entre 
    cantidad de ventas físicas de un álbum y la cantidad total de photocards 
    que pertenecen a la colección de dicho álbum.
  </p></div>
    

  
  </div>
    


</main>

<style>
    .imp-amarillo{
      color:#DCFF00;
      font-family:"Work Sans";
      font-weight: SemiBold ;
      font-size: 20px;
    }

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
    text-align: center;
    font-size: 20px;
    
  }
  .container{
    display: flex;
    justify-content: center;
  }
  .pregunta{
    display:flex;
    background-color: #02D56D;
    justify-content: center;
   }
  .lol{
    padding: 20px;
    color: black;
    text-align: center;
  }

  .highlight{
    color: #02D56D;
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
    font-size: 20px;
    font-weight: bold;
    text-align: center;
    color: #ffffff;
    margin-bottom: 100px;

  }
  .headline b {
    display: block;
  }

  #contenedor, #contenedor2 {
    position: relative;
    display: inline-block;
}

#cd {
  width: 700px;
  position: absolute;
  left:75%;
  animation: rotation 4s infinite linear;
}

@keyframes rotation {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(359deg);
  }
}

.up-down{
  animation: up-down linear 3s;
  animation-iteration-count: infinite;
  transform-origin: 50% 50%;
}

@keyframes up-down{
  0% {
    transform:  translate(1px,20px)  ;
  }
  24% {
    transform:  translate(1px,30px)  ;
  }
  50% {
    transform:  translate(1px,12px)  ;
  }
  74% {
    transform:  translate(1px,22px)  ;
  }
  100% {
    transform:  translate(1px,22px)  ;
  }
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
  .foreground_container2 {
    pointer-events: none;
    padding-left: 60%;
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
    background-color: #1a1a1a;
    /* border-radius: 20px; */
  }

  .image_container {
    display: flex;
    justify-content: start;
    align-items: center;
    height: 600px;
  }

  .d1 {
    margin-bottom: 200px;
    padding-top: 50px;
  }
  
</style>
