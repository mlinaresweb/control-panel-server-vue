<template>
  <div class="container">
    <h2>CPU</h2>
    <div class="graph-container">
      <canvas ref="chartCanvas"></canvas>
    </div>
    <div class="plate-container">
      <div class="plate">
        <div class="plate-header">
          <div class="plate-title">CPU</div>
          <div class="plate-value">{{ cpuUsage }}%</div>
        </div>
        <div class="plate-bar">
          <div class="plate-progress" :style="{ width: cpuUsage + '%' }"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Chart from 'chart.js/auto';

export default {
  name: 'CPUGraph',
  data() {
    return {
      cpuUsage: 0,
    };
  },
  mounted() {
    const data = {
      labels: ['CPU'], 
      datasets: [{
          label: 'Uso de CPU',
          data: [Math.floor(Math.random() * 100) + 1],
          backgroundColor: 'rgba(54, 162, 235, 0.2)',
          borderColor: 'rgba(54, 162, 235, 1)',
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
      this.cpuUsage = Math.floor(Math.random() * 100) + 1;
      data.datasets[0].data[0] = this.cpuUsage;
      chart.update();
    }, 3000);
  }
};
</script>

<style scoped>

 </style>