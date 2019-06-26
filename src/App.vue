<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" style="width:50px; height:50px" class="mx-auto d-block">
    <Clientes/> 
    <Taxis/>
  </div>
</template>

<script>
import Clientes from './components/Clientes.vue'
import Taxis from './components/Taxis.vue'

export default {
  name: 'app',
  components: {
    Clientes,
    Taxis
  }
}


</script>


