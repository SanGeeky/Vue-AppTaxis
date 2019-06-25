<template>
    <div class="container">
        <div class="row">
            <div class="col-md-6">
                <h4>LISTA DE PENDIENTES</h4>
                <label for="">NOMBRE</label>
                <input type="text" v-model="nombre" class="form-control">
                <label for="">DESTINO</label>
                <input type="text" v-model="destino" class="form-control">
                <h5>Tipo de carrera</h5>
                <select v-model="selected">
                    <option disabled value="">Por Favor Selecciones Uno</option>
                    <option value="100">DIURNO</option>
                    <option value="120">NOCTURNO</option>
                </select>
                <hr>
                <span>Valor Carrera: {{ selected }}</span>
                <hr>
                <button  @click="agregarCarrera()" class="btn btn-success btn-block">AGREGAR CARRERA</button>
            </div>
            <div class="col-md-6">
                <h4>LISTA DE PENDIENTES</h4>
                <ul class="list-group" v-for="(item, id) of carrerasPedientes" :key="item.id">
                    <li class="list-group-item">{{item.nombre}} <button class="btn btn-danger btn-sm float-right" @click="eliminarCarrera(id)">Eliminar</button></li> 
                </ul>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name:'TaxiClientes',
    data() {
        return {
            nombre:'',
            destino:'',
            carrerasPedientes:[],
            selected:''
        }
    },
    methods: {
        agregarCarrera(){
            this.carrerasPedientes.push({
                nombre:this.nombre,
                destino:this.destino,
                selected:this.selected
            });
            nombre:''
            localStorage.setItem('baseDatos', JSON.stringify(this.carrerasPedientes))
        },
        eliminarCarrera(id){
            this.carrerasPedientes.splice(id,1)     
            localStorage.setItem('baseDatos', JSON.stringify(this.carrerasPedientes))
        } 
    },
    created() {
        let BDStorage=JSON.parse(localStorage.getItem('baseDatos'));
        if (BDStorage===null){
            this.carrerasPedientes=[]
        }else{
            this.carrerasPedientes=BDStorage;
        }
            
    },
}
</script>
