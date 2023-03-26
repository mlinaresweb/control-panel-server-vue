<template>
    <div class="container">
      <h2>GPU</h2>
      <div class="graph-container">
      <canvas ref="chartCanvas"></canvas>
    </div>
    <div class="gpu-temperatures">
      <div class="row">
        <div  v-for="(gpu, index) in gpuTemperatures" :key="index">
          <div class="gpu-temperature">
            <span class="gpu-label">GPU {{ index + 1 }}</span>
            <span class="temperature">{{ gpu.temperature }} °C</span>
          </div>
        </div>
      </div>
    </div>
    </div>
    
  </template>
  
  
  <script>
  import Chart from 'chart.js/auto';
 

  export default {
    name: 'GPUStatsGraph',
    components: {
   
   
  },
  data() {
      return {
        gpuTemperatures: [
          { temperature: 0 },
          { temperature: 0 },
          { temperature: 0 },
          { temperature: 0 },
        ],
      };
    },
    created() {
      this.updateTemperatures();
    },
    methods: {
      updateTemperatures() {
        setInterval(() => {
          this.gpuTemperatures.forEach((gpu) => {
            gpu.temperature = this.getRandomTemperature();
          });
        }, 3000);
      },
      getRandomTemperature() {
        return Math.floor(Math.random() * (90 - 30 + 1)) + 30;
      },
    },
    mounted() {
      const data = {
        labels: [],
        datasets: [
          {
            label: 'GPU 1',
            data: [],
            backgroundColor: 'rgba(255, 99, 132, 0.2)',
            borderColor: 'rgba(255, 99, 132, 1)',
            borderWidth: 1,
            tension: 0.4,
            fill: true,
          },
          {
            label: 'GPU 2',
            data: [],
            backgroundColor: 'rgba(54, 162, 235, 0.2)',
            borderColor: 'rgba(54, 162, 235, 1)',
            borderWidth: 1,
            tension: 0.4,
            fill: true,
          },
          {
            label: 'GPU 3',
            data: [],
            backgroundColor: 'rgba(255, 206, 86, 0.2)',
            borderColor: 'rgba(255, 206, 86, 1)',
            borderWidth: 1,
            tension: 0.4,
            fill: true,
          },
          {
            label: 'GPU 4',
            data: [],
            backgroundColor: 'rgba(75, 192, 192, 0.2)',
            borderColor: 'rgba(75, 192, 192, 1)',
            borderWidth: 1,
            tension: 0.4,
            fill: true,
          },
        ],
      };
  
      const options = {
        scales: {
          y: {
            min: 0,
            max: 100,
          },
        },
      };
  
      const chartCanvas = this.$refs.chartCanvas;
      const chart = new Chart(chartCanvas, {
        type: 'line',
        data: data,
        options: options,
      });
  
      setInterval(() => {
        const gpu1 = Math.floor(Math.random() * 100) + 1;
        const gpu2 = Math.floor(Math.random() * 100) + 1;
        const gpu3 = Math.floor(Math.random() * 100) + 1;
        const gpu4 = Math.floor(Math.random() * 100) + 1;
        data.labels.push(new Date().toLocaleTimeString());
        data.datasets[0].data.push(gpu1);
        data.datasets[1].data.push(gpu2);
        data.datasets[2].data.push(gpu3);
        data.datasets[3].data.push(gpu4);
        chart.update();
      }, 3000);
    },
  };
  </script>

  
<style scoped>
.container {
  width: 70%;
  
}
.graph-container {
  height: 500px;
  position: relative;
}

canvas {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}


.gpu-temperatures {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
}

.row {
  display: flex;
  flex-wrap: wrap;
}

.gpu-temperature {
  margin-bottom: 20px;
  padding: 20px;
  background-color: rgba(54, 163, 235, 0.719);
  border-radius: 10px;
  text-align: center;
  font-size: 24px;
  color: white;
  max-width: 300px; 
  flex-basis: calc(33.33% - 20px); 
  margin-left: 20px; 
}

.gpu-temperature:last-child {
  margin-right: 0; 
}

.gpu-label {
  display: block;
  font-size: 16px;
  font-weight: bold;
  margin-bottom: 10px;
}

.temperature {
  font-size: 32px;
  font-weight: bold;
}

@media (max-width: 850px) {
  .gpu-temperature {
  width: 40px; 
  height: 115px;
  flex-basis: calc(21.11% - 20px); 
 margin-left: 10px;
}

  
.container {
    width: 80%;
    height: 400px;
  }


  .graph-container{
    height: 200px;
  }
}
@media (min-width: 1550px) {
    .graph-container {
  height: 700px;
}
}
@media (max-width: 550px) {
  .gpu-temperature {

  flex-basis: calc(10.11% - 20px); 

}
}
</style>
