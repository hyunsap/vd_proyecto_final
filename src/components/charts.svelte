<!--
	@component
	Grafico venta sin kpop
 -->
<script>
    import * as d3 from "d3"
  
    import { writable, derived } from "svelte/store";
    import {LayerCake, Svg} from "layercake"
  
    import Line from "./Line.svelte"
    import Area from "./Area.svelte"
    import AxisX from "./AxisX.svelte"
    import AxisY from "./AxisY.svelte"
  
    // Usamos csv armado
    
    import data from "./_data/ventas_evol.csv"
  
    const xKey = "año"
    const yKey = "ventas_sin_kpop"
  
    // Definimos el año como una variable reactiva
    let year = writable(2023);
  
    // Hacemos un filtro de los datos para que solo muestre hasta el año seleccionado
    const filteredData = derived(year, $year => {
      return data.filter(d => d[xKey] <= $year);
    });
  
  </script>
  
  <main>
    <div class="header">
      <h3 class="headline">
        <b>Ventas CDs occidente</b>
      </h3>
      <p class="bajada">Líneas y áreas con slider de selección</p>
   
      <!-- Slider para seleccionar el año-->
      <div class="input-container">
          <input
            type="range"
            min="2013"
            max="2023"
            step="1"
            bind:value={$year}
          /> 
          <span class="counter-container"><i>Mostrar hasta</i> <b>{$year}</b></span>
        </div>
    </div>
  
    <!-- Gráfico principal -->
    <div class="chart-container">
      <LayerCake
        padding={{ top: 8, right: 10, bottom: 20, left: 25 }}
        x={xKey}
        y={yKey}
        yDomain={[0, null]}
        data={$filteredData}
      >
        <Svg>
          <AxisX
            ticks={6}
          />
          <AxisY
            ticks={6}
          />
          <Line
            stroke = "#EACB00"
          />
          <!-- <Area
            fill = "#EFDCA3"
          /> -->
        </Svg>
        
      </LayerCake>
    </div>
  </main>

<style>   
.header {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin-top: 50px;
    margin-bottom: 30px;
  }
  .headline {
    font-size: 30px;
    line-height: 1.2;
    font-weight: normal;
    text-align: center;
    margin: 20px 0 0 0;
  }
  .bajada {
    font-size: 18px;
    font-weight: normal;
    text-align: center;
    margin: 10px 0 30px 0;
  }
  .headline b {
    display: block;
  }

  .chart-container {
    width: 500px;
    height: 400px;
    background-color: #C2E1F9;
  }

  .input-container {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 10px;
    width: 100%;
  }

  .input-container input {
    margin: 0 10px;
    -webkit-appearance: none;
    appearance: none;
    width: 200px;
    height: 5px;
    background: #ddd;
    outline: none;
    opacity: 0.7;
  }

  .input-container input::-webkit-slider-runnable-track {
    width: 100%;
    height: 5px;
    cursor: pointer;
    background: #38538A50;
  }

  .input-container input::-webkit-slider-thumb {
    border: 1px solid #000000;
    height: 15px;
    width: 15px;
    border-radius: 50%;
    background: #38538A;
    cursor: pointer;
    -webkit-appearance: none;
    margin-top: -5px;
  }
</style>