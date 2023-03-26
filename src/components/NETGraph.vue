<template>
    <div class="container">
      <h2>RED</h2>
      <div class="graph-container">
        <canvas ref="chartCanvas"></canvas>
      </div>
      <div class="container-plates">
        <div class="plate-container">
      <div class="plate">
        <div class="plate-header">
          <div class="plate-title">Subida: </div>
          <div class="plate-value">{{ uploadData }}KB</div>
        </div>
        <div class="plate-bar">
          <div class="plate-progress" :style="{ width: uploadData + '%' }"></div>
        </div>
      </div>
    </div>
    <div class="plate-container">
      <div class="plate">
        <div class="plate-header">
          <div class="plate-title">Bajada:  </div>
          <div class="plate-value">{{ downloadData }}KB</div>
        </div>
        <div class="plate-bar">
          <div class="plate-progress" :style="{ width: downloadData + '%' }"></div>
        </div>
      </div>
      </div>
    </div>
      </div>
  </template>
  
  <script>
  import Chart from 'chart.js/auto';
  
  export default {
    name: 'NETGraph',
    data() {
      return {
        uploadData: 0,
        downloadData: 0
      };
    },
    mounted() {
      const data = {
        labels: [],
        datasets: [{
          label: 'Subida',
          data: [],
          backgroundColor: 'rgba(54, 162, 235, 0.2)',
          borderColor: 'rgba(54, 162, 235, 1)',
          borderWidth: 1,
          tension: 0.4,
          fill: true
        },
        {
          label: 'Bajada',
          data: [],
          backgroundColor: 'rgba(255, 99, 132, 0.2)',
          borderColor: 'rgba(255, 99, 132, 1)',
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
        this.uploadData = Math.floor(Math.random() * 100) + 1;
        this.downloadData = Math.floor(Math.random() * 100) + 1;
        data.labels.push(new Date().toLocaleTimeString());
        data.datasets[0].data.push(this.uploadData);
        data.datasets[1].data.push(this.downloadData);
        chart.update();
      }, 3000);
    }
  };
  </script>
<style scoped>
 .container-plates{
  display: flex;
  justify-content: center;

 }
 .plate{
  width: 90%;

 }
 
 @media (max-width: 700px) {
  .plate{
  width: 50%;

 }
 .plate-header{
  font-size: 14px;
  text-align: center;
  flex-wrap: wrap;
}
.plate-value{
  font-size: 14px;
}

   }
   @media (max-width: 1024px) {
  .plate{
  padding: 15px 25px;

 }
 .plate-header{
  font-size: 14px;
  text-align: center;
  flex-wrap: wrap;
}
.plate-value{
  font-size: 14px;
}
   }
   @media screen and (min-width: 701px) and (max-width: 1035px) {
    
     .plate-container{
      margin-right: 40px ;
    }
  }
  @media screen and (min-width: 1036px) and (max-width: 1900px) {
    
    .plate-container{
     margin-right: 80px ;
   }
 }
</style>
