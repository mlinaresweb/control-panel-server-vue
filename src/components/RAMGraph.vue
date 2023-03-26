<template>
    <div class="container">
      <h2>RAM</h2>
      <div class="graph-container">
        <canvas ref="chartCanvas"></canvas>
      </div>
      <div class="plate-container">
      <div class="plate">
        <div class="plate-header">
          <div class="plate-title">RAM</div>
          <div class="plate-value">{{ ramUsage }}%</div>
        </div>
        <div class="plate-bar">
          <div class="plate-progress" :style="{ width: ramUsage + '%' }"></div>
        </div>
      </div>
    </div>
    </div>
  </template>
  
  <script>
  import Chart from 'chart.js/auto';
  
  export default {
    name: 'MemoryGraph',
    data() {
      return {
        ramUsage: 0
      };
    },
    mounted() {
      const data = {
        labels: [],
        datasets: [{
          label: 'Uso de memoria RAM',
          data: [],
          backgroundColor: 'rgba(54, 162, 235, 0.2)',
          borderColor: 'rgba(54, 162, 235, 1)',
          borderWidth: 1,
          tension: 0.4,
          fill: true
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
        type: 'line',
        data: data,
        options: options
      });
  
      setInterval(() => {
        const ramUsage = Math.floor(Math.random() * 100) + 1;
        data.labels.push(new Date().toLocaleTimeString());
        data.datasets[0].data.push(ramUsage);
        chart.update();
        this.ramUsage = ramUsage;
      }, 3000);
    }
  };
  </script>
  
  <style scoped>

  </style>
  