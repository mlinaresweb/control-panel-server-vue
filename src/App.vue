<template>
   <NavBar/>
  <ServerInfo/>
  <div class="container-graficos">
  <div class="graficos-cpu-disco">
   <CPUGraph/>
   <DISKGraph/>
  </div>
  <div class="graficos-ram-net">
    <RAMGraph/>
   <NETGraph/>
  </div>
</div>
   <GPUGraph/>
  <FooterBar/>
</template>

<script>
import CPUGraph from './components/CPUGraph.vue';
import RAMGraph from './components/RAMGraph.vue';
import DISKGraph from './components/DISKGraph.vue';
import NETGraph from './components/NETGraph.vue';
import GPUGraph from './components/GPUGraph.vue';
import ServerInfo from '/src/components/ServerInfo.vue';
import NavBar from '/src/components/NavBar.vue';
import FooterBar from '/src/components/FooterBar.vue';


export default {
  name: 'App',
  components: {
    CPUGraph,
    RAMGraph,
    DISKGraph,
    NETGraph,
    GPUGraph,
    ServerInfo,
    NavBar,
    FooterBar,
  }
}
</script>

<style>


</style>
