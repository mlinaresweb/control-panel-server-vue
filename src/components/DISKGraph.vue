<template>
    <div class="container">
        <h2>DISCO</h2>
      <div class="graph-container">
        <canvas ref="chartCanvas"></canvas>
      </div>
      <div class="plate-container">
        <div class="plate">
          <div class="plate-header">
            <div class="plate-title">Disco</div>
            <div class="plate-value">{{ diskUsage }}%</div>
          </div>
          <div class="plate-bar">
            <div class="plate-progress" :style="{ width: diskUsage + '%' }"></div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import Chart from 'chart.js/auto';
  
  export default {
    name: 'DISKGraph',
    data() {
      return {
        diskUsage: 0,
      };
    },
    mounted() {
      const data = {
        labels: ['Disco'],
        datasets: [{
          label: 'Uso de Disco',
          data: [Math.floor(Math.random() * 100) + 1],
          backgroundColor: 'rgba(54, 162, 235, 0.2)',
          borderColor: 'rgba(75, 192, 192, 1)',
          borderWidth: 1,
          fill: false,
        }]
      };
      
      const options = {
        scales: {
          y: {
            min: 0,
            max: 100
          }
        }
      };
      
      const chartCanvas = this.$refs.chartCanvas;
      const chart = new Chart(chartCanvas, {
        type: 'bar', 
        data: data,
        options: options
      });
      
      setInterval(() => {
        this.diskUsage = Math.floor(Math.random() * 100) + 1;
        data.datasets[0].data[0] = this.diskUsage;
        chart.update();
      }, 3000);
    }
  };
  </script>
  
  <style scoped>

  </style>