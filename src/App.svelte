<script>
    import Scroller from "@sveltejs/svelte-scroller"
    import {onMount} from "svelte"
    import * as d3 from "d3"
    import DebugScroller from "./components/DebugScroller.svelte"

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
    let pc_colec = ["images/pcs/pcs0.png", "images/pcs/pcs1.png", "images/pcs/pcs2.png", "images/pcs/pcs2.png", "images/pcs/pcs2.png", "images/pcs/pcs3.png", "images/pcs/pcs4.png", "images/pcs/pcs5.png", "images/pcs/pcs6.png", "images/pcs/pcs7.png", "images/pcs/pcs8.png"]
    let i = 0
    let i0 = 0

    /* Charts */
    let charts_ventas = {
        0: "/images/grafVentas/ventas1.png",
        1: "/images/grafVentas/ventas2.png",
        2: "/images/grafVentas/ventas3.png",
        3: "images/grafVentas/ventas4.png"
    }

    let chart_top = {0: "/images/grafAlbums/zero2.png",1: "/images/grafAlbums/prim2.png",2:"/images/grafAlbums/segun2.png",3:"/images/grafAlbums/ter2.png",4:"/images/grafAlbums/cuar2.png",
      5:"/images/grafAlbums/quinto2.png", 6:"/images/grafAlbums/sext2.png",7:"/images/grafAlbums/sept2.png",8:"/images/grafAlbums/oct2.png",9:"/images/grafAlbums/nov2.png",
      10:"/images/grafAlbums/dec2.png",11:"/images/grafAlbums/once2.png",12:"/images/grafAlbums/doce2.png",13:"/images/grafAlbums/trece2.png",14:"/images/grafAlbums/cator2.png",
      15:"/images/grafAlbums/quince2.png",16:"/images/grafAlbums/dcseis2.png",17:"/images/grafAlbums/dcsiet2.png",18:"/images/grafAlbums/dcocho2.png",
      19:"/images/grafAlbums/dcnuev2.png",20:"/images/grafAlbums/veinte2.png",21:"/images/grafAlbums/vntuno2.png"}

    let chart_tendencia_ventas = "/images/tendencia_ventas_punt_pcs.png"
    let chart_ganancia_ventas = "/images/ganancia_ventas.png"

    let contador_fichas = {0:"/images/botones/contador-fichas0.png", 1:"/images/botones/contador-fichas1.png",
      2:"/images/botones/contador-fichas2.png", 3:"/images/botones/contador-fichas3.png",
      4:"/images/botones/contador-fichas4.png", 5:"/images/botones/contador-fichas5.png", 
      6:"/images/botones/contador-fichas6.png", 7:"/images/botones/contador-fichas7.png",
      8:"/images/botones/contador-fichas8.png", 9:"/images/botones/contador-fichas9.png",
      10:"/images/botones/contador-fichas10.png", 
    }

    function handleButtonClick() {
        const textoAnimado = document.createElement("div");
        textoAnimado.className = "animated-text";
        textoAnimado.textContent = "-$10k";
        if (i0 < pc_colec.length-1){
          i0=i0+1;
        }
        else {
          textoAnimado.textContent = "Sin fichas";
          i0=pc_colec.length-1;
        }

        const contenedor = document.getElementById("contenedor0");
        contenedor.appendChild(textoAnimado);

        // Eliminar el texto animado después de la animación
        setTimeout(() => {
            contenedor.removeChild(textoAnimado);
        }, 1000);
    }

    function handleButtonClickWithPhotocard() {
        const textoAnimado = document.createElement("div");
        const textoAnimado2 = document.createElement("div");
        textoAnimado.className = "animated-text";
        textoAnimado2.className = "animated-text2";      
        if (i < pc_colec.length-1){
          if (i===2 || i===3 || i===6 || i===9){
            textoAnimado2.textContent = "Repetida";
            textoAnimado2.style ="color: red";
          }
          else{
            textoAnimado2.textContent = "+1 photo";
          } 

          i=i+1;
          textoAnimado.textContent = "-$10k";
        }

        else {
          textoAnimado.textContent = "Sin fichas";
        }


        const contenedor = document.getElementById("contenedor1");
        contenedor.appendChild(textoAnimado);
        const contenedor2 = document.getElementById("contenedor2");
        contenedor2.appendChild(textoAnimado2);
        // Eliminar el texto animado después de la animación
        setTimeout(() => {
            contenedor.removeChild(textoAnimado);
            contenedor2.removeChild(textoAnimado2);
        }, 1000); 
    }

    onMount(()=>{})
</script>

<main>

    <div class="header">
      <img src="/images/portada.png" width="100%" alt="portada" >
      <img src="/images/noeasy-cd.png" id='cd' alt="cd">
    </div>

    <div class="content">
      <div class="d1">
        <div style="display: flex; align-items:center;flex-direction:column; margin-left:20%; margin-right:20%; margin-bottom:400px; margin-top:100px">
          <h3 class="lol" style="width:900px; background-color: #9FF52B; height:30px; text-align:center; justify-content:center; color: black; font-family: Work Sans; margin-bottom:100px">EXPLORANDO EL EFECTO DEL CONSUMISMO FAN EN LA VENTA DE DISCOS FÍSICOS</h3>
          <p>En un contexto mundial de dominancia del streaming respecto a otros formatos de consumo musical, las ventas de discos se encuentran en bajada. <br><br> Pero, sorprendentemente, hay un segmento de la industria se estan observando diferentes resultados.</p>
        </div>
        <div class="bajada">
          <p>Para entender lo que esta sucediendo hoy en día con la venta de álbumes físicos, primero es <br>importante fijarse en como son estos. </p>
        </div>
        <div><h3 class="imp-amarillo">EXPLOREMOS LA EXPERIENCIA ACTUAL DE COMPRAR UN ALBUM</h3></div>
        <img src="/images/botones/flechas.svg" class="up-down" width=30px alt="flechas">
      </div>
      <!-- <br><br><br><br><br> -->
      <div class="espacio" style="height:200px"></div>
    <div class="gamification_portion">
      <img src="public/images/botones/disclaimer.png" width=500px alt="advert">
      <img src="public/images/botones/disclaimer2.png" width=100px alt="advert2" style="display: flex; position: relative; bottom: 220px; left:20%">
      <img src="/images/botones/flechas.svg" class="up-down" width=30px alt="flechas">
      <div class="espacio" style="height: 200px"></div>      

        <div class="album_no_pcs">
            <br>
            <div class="container"><div class="juego" style="width: 800px"><h3 style="font-family: Lato;font-size: 20px; text-align: center; color: #ffffff">Vamos a jugar un juego<br>
              Tenes disponibles 100.000 fichas, podes canjearlas como quieras</h3></div></div>
            <div class="ficha" style="display:flex; justify-content: center">
              <img src="images/botones/fichas.png" width=100px alt="ficha"></div>
            <div class="container"><div class="juego" style="width: 800px"><h3 style="font-family: Lato;font-size: 20px; text-align: center; color: #ffffff">
              La única regla es que en cada sección solo podes comprar los álbumes que te alcancen, cuando se te acaben las fichas vas a tener que seguir scrolleando.</h3></div>
            </div>
            <div class="espacio" style="height:200px"></div>

            
            <p>Tenés la posibilidad de comprar el álbum de Taylor Swift "1989 (Taylor's Version)". <br>Compra tantos álbumes como quieras</p>
            <br>
            <img src={contador_fichas[i0]} alt="contador" style="position: absolute; width: 100px; padding-left: 400px">
            <img src="/images/albums/1989_taylor.png" width=300px margin-top=10px alt="ts">
            <br>
            <img src="/images/botones/boton_canjear.png" width=120px class="botonImagen" alt="boton" on:click={handleButtonClick}>
            <div id="contenedor0"></div>           
            <br><br>
            <div><h3 class="imp-amarillo">CUANDO TERMINES SCROLLEA A LA SIGUIENTE SECCIÓN</h3></div>
        </div>

        <div class="reinicio" style="display: flex; flex-direction:column; height: 1000px; justify-content: center; align-items: center">
          <div class="reinicio2" style="width: 800px">
            <p>En caso de que te hayas gastado todas las fichas, se reinician, <br>volvés a tener 100.000 fichas disponibles para canjear</p>
          </div>
          <img src="images/botones/fichas.png" width=100px alt="ficha">        
        </div>

        <div class="album_pcs">
            <p>Ahora tenés la posibilidad de comprar el álbum de Stray Kids “ROCK-STAR”<br>
              Tu objetivo es conseguir la foto de I.N, cuyo nombre se encuentra en el reverso
             <br> Nuevamente comprá cuantos quieras</p>
             <img src={contador_fichas[i]} alt="contador" style="position: relative; width: 100px; right: 350px">
             <div class="cero_pcs" style="display:flex; align-items: center; column-gap: 100px; margin-bottom:10px">
                <img src="/images/albums/rockstar.png" width=300 alt="skz" style="position:relative; left: 14%">
                <img id="img_pc" src={pc_colec[i]} width=500 alt="pcs" style="position:relative; left: 10%">
            </div>
            <img src="/images/botones/boton_canjear.png" width=120px class="botonImagen" alt="boton" on:click={handleButtonClickWithPhotocard}>
            <div id="contenedor1"></div>
            <div id="contenedor2"></div>           
           
        </div>
    </div>

    <br><br>

    <div class="story">

      <div class="container">
        <div class="pregunta2" style="display:flex; flex-direction:column; margin-top:100px; margin-left:120px; align-items:center">
          <h3 class="lol" style="background-color: #9FF52B; height:30px; align-items:center; color: black; font-family: Work Sans">Y esto... ¿De qué sirve? ¿Para qué querría yo fotos de otra gente?</h3>
          <p style="margin-top:50px; margin-bottom:100px; width:100%; text-aling:center; font-family: Work Sans">Esas "fotos de otra gente" son las llamadas photocards, estas son pequeños cartones impresos con fotos. 
          <br><br>También podrías preguntarte porque tanto escandalo por una foto, las photocards son artículos coleccionables en el mundo del K-pop, 
          algo así como las cartas de Pokémon o las figuritas del álbum del mundial. Se incluyen en los álbumes de kpop como regalo, 
          pero como en los sobres de figuritas, no vienen todas en todos los álbumes</p>
      </div>

      <div class="container">

      </div>
    </div>

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
          <img src={charts_ventas[index]} alt="charts_ventas" style="width: 450px; padding-left: 50px">
        </div>
        <div slot="foreground" class="foreground_container">
          <section class="step_foreground">
            <div class="epi_foreground">
              <h3 style="color: #4DB5FF">¿Cómo se ve el mercado de ventas en música?</h3>
              <p>Las ventas de álbumes occidentales, principalmente de Estados Unidos y Europa, en la última década presentan una baja
                de ventas físicas gradual, en gran parte causada por la aparición de los 
                servicios de streaming.
              </p>
            </div>
          </section>
          <section class="step_foreground">
            <div class="epi_foreground">
              <h3 style="color: #FF0F9A">¿Qué diferencia se encuentra en kpop?</h3>
              <p>Por el contrario, las ventas en kpop cada año aumentan de manera exponencial,
                ya que ofrecen una experiencia de consumidor más personalizada y llamativa.
                Todo el diseño del álbum y sus inclusiones están pensados para la venta masiva.
              </p>
            </div>
          </section>
          <section class="step_foreground">
            <div class="epi_foreground">
              <h3 style="color: #DCFF00">¿Cómo se afecta al mercado actual?</h3>
              <p>Se ha llegado a un punto en el que la venta de álbumes de kpop ha superado
                a los álbumes del resto de la industria musical.</p>
            </div>
          </section>
          <section class="step_foreground">
            <div class="epi_foreground">
              <h3 style="color: #DCFF00">¿Cómo se afecta al mercado actual?</h3>
              <p>De hecho, a partir de 2020 el mercado físico de álbumes experimenta una repuntada notable, 
                en gran parte motivada por los álbumes de kpop.</p>
            </div>
          </section>
        </div>
      </Scroller>
    </div>
    <br><br>
    <div class="top20" style="display:flex; flex-direction:column; margin-right:100px; margin-left: 100px;align-items:center">
      <h3 class="lol" style="background-color: #9FF52B; height:30px; align-items:center; color: black; font-family: Work Sans;margin-top:100px">¿LA CANTIDAD DE PHOTOCARDS IMPORTAN?</h3>
      <h3 class="imp-amarillo" style="margin-top: 80px;">TOP 20: ÁLBUMES MÁS VENDIDOS DE 2023</h3>
      <p style="width: 70%; margin-bottom:0px">A partir de la lista de IFPI de los discos con mayores ventas físicas de 2023, se analiza la popularidad de un álbum, 
        determinado a partir de las ventas físicas totales sobre la cantidad de streams en Spotify de cada álbum en 2023, 
        y su correlación con la cantidad de photocards presentes, 
        en particular cuántos álbumes habría que comprar para completar la colección si no hubiera repeticiones.
      </p>
    </div>
  
    <div class="espacio" style="height:200px"></div>
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
  <div slot="background" class="background_container">
    <img src={chart_top[index2]} alt="dad" width=600px>
  </div>
  <div slot="foreground" class="foreground_container2">
    <section class="step_foreground"><div class="epi_foreground2">Esta es la distribución de popularidad de ventas a partir de las photocards de los 20 álbumes más vendidos de 2023: en rosa aquellos que son de kpop y en azul el que no lo es. <br>Exploremos cómo se ve el top 20...</div></section>
    <section class="step_foreground"><div class="epi_foreground2">1° puesto: <br>FML - Seventeen<br>
      Popularidad(ventas/streams): 18<br>
      Ventas: 6.4 millones<br>
      Streams: 360 millones<br>
      Photocards totales: 72<br>
      Photocards incluidas: 2<br>
    </div></section>
    <section class="step_foreground"><div class="epi_foreground2">2° puesto: <br>5-Star - Stray Kids<br>
      Popularidad (ventas/streams): 9<br>
      Ventas: 5.3 millones<br>
      Streams: 596 millones<br>
      Photocards totales: 24<br>
      Photocards incluidas: 2<br>
    </div></section>
    <section class="step_foreground"><div class="epi_foreground2">3° puesto: <br>ISTJ - NCT Dream<br>
      Popularidad (ventas/streams): 29<br>
      Ventas: 4.5 millones<br>
      Streams: 160 millones<br>
      Photocards totales: 14<br>
      Photocards incluidas: 1<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">4° puesto: <br>Seventeenth Heaven - Seventeen
      <br>Popularidad (ventas/streams): 37
      <br>Ventas: 4.5 millones
      <br>Streams: 120 millones
      <br>Photocards totales: 72
      <br>Photocards incluidas: 2
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">5° puesto: <br>Rockstar - Stray Kids<br>
      Popularidad (ventas/streams): 13<br>
      Ventas: 4.2 millones<br>
      Streams: 313 millones<br>
      Photocards totales: 16<br>
      Photocards incluidas: 1<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">6° puesto: <br>1989 (Taylor’s Version) - Taylor Swift<br>
      Popularidad (ventas/streams): 1<br>
      Ventas: 2.8 millones<br>
      Streams: 3075 millones<br>
      Photocards totales: 0<br>
      Photocards incluidas: 0<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">7° puesto: <br>Golden - Jungkook<br>
      Popularidad (ventas/streams): 1<br>
      Ventas: 2.7 millones<br>
      Streams: 3042 millones<br>
      Photocards totales: 4<br>
      Photocards incluidas: 2<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">8° puesto: <br>Exist - EXO<br>
      Popularidad (ventas/streams): 17<br>
      Ventas: 2.3 millones<br>
      Streams: 134 millones<br>
      Photocards totales: 24<br>
      Photocards incluidas: 1<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">9° puesto: <br>I’ve Mine - IVE<br>
      Popularidad (ventas/streams): 12<br>
      Ventas: 2.2 millones<br>
      Streams: 187 millones<br>
      Photocards totales: 12<br>
      Photocards incluidas: 1<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">10° puesto: <br>Layover - V<br>
      Popularidad (ventas/streams): 2<br>
      Ventas: 2.2 millones<br>
      Streams: 1313 millones<br>
      Photocards totales: 15<br>
      Photocards incluidas: 5<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">11° puesto: <br>Youth in the Shade - Zerobaseone<br>
      Popularidad (ventas/streams): 24<br>
      Ventas: 2.1 millones<br>
      Streams: 87 millones<br>
      Photocards totales: 36<br>
      Photocards incluidas: 1<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">
      12° puesto: <br>My World - aespa<br>
      Popularidad (ventas/streams): 9<br>
      Ventas: 2.1 millones<br>
      Streams: 239 millones<br>
      Photocards totales: 8<br>
      Photocards incluidas: 1<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">13° puesto: <br>The Name Chapter: Freefall - TXT<br>
      Popularidad (ventas/streams): 7<br>
      Ventas: 2 millones<br>
      Streams: 268 millones<br>
      Photocards totales: 15<br>
      Photocards incluidas: 1<br>
       </div></section>
    <section class="step_foreground"><div class="epi_foreground2">14° puesto: <br>I Feel - (G)I-dle<br>
      Popularidad (ventas/streams): 6<br>
      Ventas: 2 millones<br>
      Streams: 339 millones<br>
      Photocards totales: 15<br>
      Photocards incluidas: 1<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">15° puesto: <br>Fact Check - NCT 127<br>
      Popularidad (ventas/streams): 22<br>
      Ventas: 1.9 millones<br>
      Streams: 88 millones<br>
      Photocards totales: 27<br>
      Photocards incluidas: 1<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">16° puesto: <br>Dark Blood - Enhypen<br>
      Popularidad (ventas/streams): 4<br>
      Ventas: 1.7 millones<br>
      Streams: 404 millones<br>
      Photocards totales: 21<br>
      Photocards incluidas: 1<br>
       </div></section>
    <section class="step_foreground"><div class="epi_foreground2">17° puesto: <br>I’ve IVE - IVE<br>
      Popularidad (ventas/streams): 4<br>
      Ventas: 1.7 millones<br>
      Streams: 479 millones<br>
      Photocards totales: 18<br>
      Photocards incluidas: 1<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">18° puesto: <br>Face - Jimin<br>
      Popularidad (ventas/streams): 2<br>
      Ventas: 1.7 millones<br>
      Streams: 1889 millones<br>
      Photocards totales: 6<br>
      Photocards incluidas: 1<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">19° puesto: <br>Orange Blood - Enhypen<br>
      Popularidad (ventas/streams): 12<br>
      Ventas: 1.7 millones<br>
      Streams: 141 millones<br>
      Photocards totales: 28<br>
      Photocards incluidas: 2<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">
      20° puesto: <br>Drama - aespa<br>
      Popularidad (ventas/streams): 7<br>
      Ventas: 1.5 millones<br>
      Streams: 224 millones<br>
      Photocards totales: 8<br>
      Photocards incluidas: 1<br>
      </div></section>
    <section class="step_foreground"><div class="epi_foreground2">Este es el top 20 de álbumes con más ventas físicas de 2023, en el cual se puede apreciar cierta correlación entre la popularidad de ventas y la cantidad de photocards.</div></section>
  </div>
  </Scroller>
  
  <div class="container" style="margin-top: 400px">
    <div class="pregunta2" style="display:flex; flex-direction:column; margin-top:100px; align-items:center; margin-top:100px; background-color:black">
      <p style="margin-top:50px; margin-bottom:200px; width:80%; text-aling:center; font-family: Work Sans">En definitiva posible ver que este fenómeno encuentra su explicación en las photocards, 
        hay una correlación bastante fuerte entre cantidad de ventas físicas de un álbum y la cantidad total de photocards que pertenecen a la colección de dicho álbum.
        No es coincidencia que los álbumes que lideran y ocupan prácticamente todo el top 20 sean álbumes de kpop, y solo Taylor Swift, que es la artista más exitosa hoy en día, 
        haya logrado entrar a este top.
      </p>
      <p style="width:60%; text-aling:center; font-family: Work Sans">
        Aunque el hecho de que las ventas de discos físicos esten creciendo en la industria musical es algo bueno, no todo es color de rosas.
        <br> <br> Nosotros consideramos la cantidad de álbumes que deberías comprar suponiendo que <br>nunca se repitieran las photocards al abrir álbumes.
      </p>
      <h3 class="imp-amarillo" style="margin-bottom: 200px;">¿QUE PASARÍA SI ESTAS SE REPITIERAN?</h3>
  </div>
  </div>

  <footer class="footer">
    <div class="text_ft">
      <p class="text"> by Maru y Emi</p>
    </div>
    <div class="contenido">
      <div class="links">
        <a href="https://github.com/hyunsap/vd_proyecto_final" target="_blank"><img src="/images/github.svg" alt="logo github" style="width: 40px; height:40px; margin-right:15px"></a>
        <a href="https://www.figma.com/design/OZ0bkh8UFGvNlxOPplalrv/Final?node-id=0-1&t=gKrjFSp326bvUV2w-1" target="_blank"><img src="/images/figma.svg" alt="logo figma" style="width: 40px; height:40px"></a>
      </div>
      <div><p id="link"> LINKS DEL PROYECTO </p></div>
    </div>
  </footer>


</main>

<style>
    h3{
      font-family: "Work Sans";
      font-size: 20px; 
      text-align: center; 
      color: #ffffff

    } 
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
    margin: 50px;
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

  .botonImagen{
    cursor:pointer;
  }

  .bajada {
    font-family: "Work Sans";
    font-size: 20px;
    font-weight: bold;
    text-align: center;
    color: #ffffff;
    margin-bottom: 100px;

  }

  #contenedor0, #contenedor1 {
    position: relative;
    display: inline-block;
    bottom: 45px;
    left: 20px;
    width: 100px;
  }

  #contenedor0{
    bottom: 35px;
  }

  #contenedor2 {
    position: relative;
    display: inline-block;
    bottom: 25px;
    right:82px;
    width:100px
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
    /* padding-left: 50%; */
    padding-right: 80px;
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

  .epi_foreground2 {
    padding: 20px;
    max-width:300px;
    background-color: #0068B3;
    color: #FFFD02;
    /* border-radius: 20px; */
  }

  .image_container {
    display: flex;
    justify-content: start;
    align-items: center;
    height: 600px;
  }

  .background_container{
    display: flex;
    justify-content: start;
    padding-left: 50px;
  }

  .d1 {
    margin-bottom: 150px;
    padding-top: 150px;
  }

  .footer {
	display: flex;
  flex-direction: row;
  column-gap: 1000px;
  justify-content: center;
  align-items: center;
  width: 115%;
  margin-top: 100px;
  margin-bottom: -10px;
  margin-left: -100px;
  padding-right: 18px;
  height: 100px;
  background-color: #0068B3;
  }
.text_ft{
  display: flex;
  align-items: center;
  margin-left: 40px;
  height: 60px;
  padding-left: 10px;
}
#link{
  font-size: 15px;
  font-family:"Work Sans";
  font-weight: bold;
  color: white;
}
.contenido{
  display: flex;
  flex-direction: row;
  column-gap: 30px;
}
.text{
  color: #DEFF4E;
  font-size: 20px;
  font-family:"Work Sans";
  font-weight: bold;
  text-align: center;
}

  
</style>
