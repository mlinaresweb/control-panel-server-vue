<template>
  <div class="server-info">
    <h2 class="server-info__title">Información del servidor </h2>
    <div class="server-info__content">
      <div class="server-info__section">
        <h3 class="server-info__subtitle">Servidor</h3>
        <hr>
        <p class="server-info__text">{{ serverName }}</p>
      </div>
      <div class="server-info__section">
        <h3 class="server-info__subtitle">Tiempo encendido</h3>
        <hr>
        <p class="server-info__text">{{ uptime }}</p>
      </div>
      <div class="server-info__section">
        <h3 class="server-info__subtitle">Memoria RAM</h3>
        <hr>
        <p class="server-info__text">{{ ram }}</p>
      </div>
      <div class="server-info__section">
        <h3 class="server-info__subtitle">Capacidad de almacenamiento</h3>
        <hr>
        <p class="server-info__text">{{ storage }}</p>
      </div>
      <div class="server-info__section">
        <h3 class="server-info__subtitle">GPU</h3>
        <hr>
        <p class="server-info__text">{{ gpu }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      uptime: "",
      ram: "",
      storage: "",
      gpu: "",
      serverName: "Servidor 1",
    };
  },
  mounted() {
    this.uptime = "1h 23m"; 
    this.ram = "4 x Corsair Vengeance LPX DDR4 3200MHz PC4-25600 64GB"; 
    this.storage = "1 x Toshiba N300 NAS 3.5 8 TB SATA 3";
    this.gpu = "4 x MSI GeForce RTX 3090 VENTUS 3X OC 24GB GDDR6X"; 
  },
};
</script>
  
  <style scoped>
 hr{
  color: white;
  border: 1px solid;
  margin-bottom: 5px;
}

.server-info {
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.274);
  padding: 20px;
  margin: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.server-info__title {
  font-size: 2em;
  font-weight: bold;
  margin-bottom: 5px;
}

.server-info__content {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.server-info__section {
  background-color: rgba(54, 163, 235, 0.719);
  border-radius: 8px;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.39);
  margin: 10px;
  padding: 20px;
  text-align: center;
  max-width: 200px;
}

.server-info__subtitle {
  color: white;
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 10px;
}

.server-info__text {
  color: white;
  font-size: 20px;
  margin: 0;
}

.server-info__plate {
  background-color: #444;
  color: white;
  font-size: 18px;
  font-weight: bold;
  text-align: center;
  padding: 10px 20px;
  border-radius: 20px;
  margin-top: 20px;
}

@media (max-width: 768px) {
  .server-info {
    margin: 20px 0;
  }

  .server-info__title {
    font-size: 24px;
  }

  .server-info__content {
    flex-direction: column;
    align-items: center;
  }

  .server-info__section {
    max-width: none;
    width: 90%;
    margin: 10px 0;
  }
}
  </style>
  
  