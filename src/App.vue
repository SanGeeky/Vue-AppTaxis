<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" style="width:50px; height:50px" class="mx-auto d-block">
    <TaxisClientes /> 
    <Taxis/>
  </div>
</template>

<script>
import TaxisClientes from './components/TaxisCliente.vue'
import Taxis from './components/Taxis.vue'

export default {
  name: 'app',
  components: {
    TaxisClientes,
    Taxis
  }
}


</script>


