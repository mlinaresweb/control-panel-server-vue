<template>
    <footer class="footer">
      <div class="footer-content">
        <p>&copy; {{ currentYear }} Manel Linares. Todos los derechos reservados.</p>
        <div class="footer-made">
        <div class="footer-logos">
          <img src="../assets/icons8-vue-js-48.png" alt="Vue.js logo" />
          <img src="../assets/chartjs.png" alt="Chart.js logo" />
        </div>
        <p>Hecho con Vue.js & Chartjs</p>
    </div>
    <div class="social">
          <a href="https://github.com/mlinaresweb" target="_blank">
            <img src="../assets/github.png" alt="Icono GitHub" />
          </a>
          <a href="https://www.linkedin.com/in/manellinares/" target="_blank">
            <img src="../assets/linkedin.png" alt="Icono LinkedIn" />
          </a>
        </div>
      </div>
    </footer>
    
  </template>
  
  <script>
  export default {
    name: 'FooterBar',
    data() {
      return {
        currentYear: new Date().getFullYear()
      };
    }
  };
  </script>
  
  <style scoped>
  .footer {
    background-color: rgba(54, 163, 235, 0.719);
    color: #fff;
    padding: 30px;
    text-align: center;
    display: flex;
    justify-content: space-around;
  }
  
  .footer p {
    margin: 0 0 20px;
  }
  
  .footer-logos img {
    height: 30px;
    margin-left: 10px;
  }
  </style>
  