<template>
  <div id="app" class="p-4">
    <TaxisClientes/> 
    <h3 class="text-center">taxis de la empresa</h3>
    <ListaTaxis/>
  </div>
</template>

<script>
import TaxisClientes from './components/TaxisClientes'
import ListaTaxis from './components/ListaTaxis'

export default {
  name: 'app',
  components: {
    TaxisClientes,
    ListaTaxis
  }
}
</script>