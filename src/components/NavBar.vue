<template>
  <nav class="navbar" ref="navbar">
    <div class="navbar-brand" @click="toggleSidebar">
      <img src="../assets/icons8-menú-50.png" alt="logo" width="30" height="30">
    </div>
    <div class="navbar-right">
      <img src="../assets/icons8-ajustes-32.png" alt="settings" width="28" height="28">
      <img src="../assets/icons8-reiniciar-50.png" alt="restart" width="24" height="24">
      <img src="../assets/icons8-apagar-30.png" alt="power" width="28" height="28">
    </div>
    <div class="sidebar" :class="{ open: sidebarOpen }">
      <ul>
        <li><a href="#">Dashboard</a></li>
        <li><a href="#">Manual</a></li>
        <li><a href="#">Información</a></li>
        <li><a href="#">Notificaciones</a></li>
      </ul>
      <div class="close-sidebar" @click="closeSidebar">
        <img src="../assets/icons8-salida-50.png" alt="close" width="24" height="24">
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      sidebarOpen: false
    };
  },
  methods: {
    toggleSidebar() {
      this.sidebarOpen = !this.sidebarOpen;
    },
    closeSidebar() {
      this.sidebarOpen = false;
    },
    handleScroll() {
      if (this.sidebarOpen && window.pageYOffset > 0) {
        this.sidebarOpen = false;
      }
    }
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll);
  }
};
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: rgba(54, 163, 235, 0.719);
  color: white;
  height: 60px;
  width: 100%;
}

.navbar-brand img {
  cursor: pointer;
  margin-left: 20px;
}

.navbar-right {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 7px;
  margin-right: 15px;
  cursor: pointer;
}

.sidebar {
  position: fixed;
  top: 60px;
  left: -100%;
  width: 200px;
  height: 100%;
  background-color: rgba(54, 163, 235, 0.719);
  color: white;
  transition: left 0.5s;
}

.sidebar.open {
  left: 0;
}

ul {
  list-style: none;
  padding-left: 0;
}

li {
  margin-bottom: 10px;
}

a {
  display: block;
  color: white;
  text-decoration: none;
  padding: 10px;
  transition: background-color 0.3s;
}

a:hover {
  background-color: #ffffff;
  color:rgba(54, 163, 235, 0.719) ;
}

.close-sidebar img {
  margin-left: 10px;
  cursor: pointer;
}
</style>