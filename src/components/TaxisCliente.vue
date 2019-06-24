<template>
    <div class="container">
        <div class="row">
            <div class="col-md-6">
                <h4>Cliente</h4>
                <label for="">Nombre Usuario</label>
                <input v-model="nombre" type="text" class="form-control">
                <label for="">Destino</label>
                <input v-model="destino" type="text" class="form-control">
                <hr>
                <select v-model="modalidad">
                <option disabled value="">Seleccione Carrera</option>
                    <option value="120">Diurno</option>
                    <option value="150">Nocturno</option>
                </select>
                <hr>
                <span>Precio: {{ modalidad }}</span>
                <hr>
                <button v-on:click="agregarCarrera" class="btn btn-success btn-block">Carrera</button>
            </div>
            <div class="col-md-6">
                <h4>Lista de Carreras</h4>
                <br>
                <ul v-for="item of carreras" :key="item.id" class="list-group">
                <li class="list-group-item">{{ item.nombre }} - {{ item.telefono }}
                    <button v-on:click="eliminarCarrera(item)" class="btn btn-danger float-right btn-sm">Eliminar</button>
                </li>
                </ul>
            </div>
        </div>
        <h1>{{ nombre }}</h1>
        <h1>{{ destino }}</h1>
    </div>
</template>

<script>
import { METHODS } from 'http';
import { log } from 'util';
export default {
    name: 'TaxisClientes',
    data(){
        return{
            nombre:'',
            telefono:'',
            destino:'',
            modalidad:'',
            carreras:[]
        } 
    },
    methods:{
        agregarCarrera()
        {
            this.carreras.push({nombre: this.nombre, destino: this.destino})
            console.log(this.carreras);
            this.nombre=''
            this.destino=''
            localStorage.setItem('DataBase', JSON.stringify(this.carreras))
        },
        eliminarCarrera(index)
        {
            this.carreras.splice(index,1);   
            console.log(this.carreras);
            localStorage.setItem('DataBase', JSON.stringify(this.carreras))            
        }
    },
    created(){
        let DBStorage = JSON.parse(localStorage.getItem('DataBase'))
        if(DBStorage === null){
            this.carreras=[]
        }
        else{
            this.carreras = DBStorage;
        }
    }


}
</script>


