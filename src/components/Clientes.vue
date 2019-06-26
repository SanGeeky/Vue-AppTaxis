<template>
    <div class="container">
        <div class="row">
            <div class="col-md-6">
                <h4>Cliente</h4>
                <label for="">Nombre Usuario</label>
                <input v-model="nombre" type="text" class="form-control">
                <label for="">Teléfono</label>
                <input v-model="telefono" type="text" class="form-control">
                <label for="">Destino</label>
                <input v-model="destino" type="text" class="form-control">
                <hr>
                <div class="form-row">
                    <div class="form-col">
                        <select v-model="modalidad" class="form-control">
                            <option disabled value="">Modalidad Carrera</option>
                            <option value="Diurno">Diurno</option>
                            <option value="Nocturno">Nocturno</option>
                         </select>
                    </div>
                    <div class="col">                
                         <button v-on:click=" !horas ? horas=true:horas=false"  :class="horas ? 'btn btn-success btn-block':'btn btn-danger btn-block'" style="margin-left:5px;">Servicio Horas</button>     
                    </div>
                    <div class="col">
                        <input v-if="horas===true" v-model="numeroHoras" type="number" class="form-control" style="margin-left:2.5px;" placeholder="Numero Horas">
                    </div>
                </div>
                <hr>
                <span>Precio: {{ CalcularValor }}</span>
                <hr>
                <button v-on:click="agregarCarrera"  class="btn btn-success btn-block">Carrera</button>
                <br>
            </div>
            <div class="col-md-6">
                <h4>Lista de Carreras</h4>
                <br>
                <ul v-for="(item,index) of carreras" :key="item.id" class="list-group">
                <li  class="list-group-item">
                    <span v-if="item.horas === 0" >{{ index+1 }}.- <b>Nombre:</b> {{ item.nombre }} <b>Telefono:</b> {{ item.telefono }} <b>Destino:</b> {{ item.destino }} <br> <b>Modalidad:</b> {{ item.modalidad }} <b>Total:</b> {{ item.total }}</span>
                    <span v-if="item.horas >= 1" >{{ index+1 }}.- <b>Nombre:</b> {{ item.nombre }} <b>Telefono:</b> {{ item.telefono }} <b>Destino:</b> {{ item.destino }} <br> <b>Modalidad:</b> {{ item.modalidad }} <b>Horas:</b> {{ item.horas }} <b>Total:</b> {{ item.total }}</span>                    
                    <button v-on:click="eliminarCarrera(index)" class="btn btn-danger float-right btn-sm">Eliminar</button>
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
    name: 'Clientes',
    data(){
        return{
            nombre:'',
            telefono:'',
            destino:'',
            modalidad:'',
            precio:0,
            horas:false,
            numeroHoras:0,
            valorCarrera:0,
            carreras:[]
        } 
    },
    methods:{
        agregarCarrera()
        {
            // if(this.horas)
            //     this.carreras.push({nombre: this.nombre, telefono: this.telefono,destino: this.destino, modalidad: this.modalidad, total: this.valorCarrera})
            // else
            if((this.horas == true && this.numeroHoras>0) || (this.horas == false && this.numeroHoras == 0) && this.modalidad!='')
             this.carreras.push({nombre: this.nombre, telefono: this.telefono,destino: this.destino, modalidad: this.modalidad, horas: this.numeroHoras, total: this.valorCarrera})            
            console.log(this.carreras);
            this.nombre=''
            this.telefono=''
            this.destino=''
            this.modalidad=''
            this.horas=false
            this.numeroHoras=0
            this.valorCarrera=0
            localStorage.setItem('DataBase', JSON.stringify(this.carreras))
        },
        eliminarCarrera(index)
        {
            this.carreras.splice(index,1);   
            console.log(this.carreras);
            localStorage.setItem('DataBase', JSON.stringify(this.carreras))            
        }
    },
     computed:{
        CalcularValor: function(){
            
            if(this.modalidad==='Diurno')
            {
                if(this.horas)
                    this.precio=5000
                else
                    return this.valorCarrera = this.precio=1000
            }
            else if(this.modalidad==='Nocturno')
            {
                if(this.horas)
                    this.precio=8000
                else
                    return this.valorCarrera = this.precio=2000
            }
            else
                this.precio = 0
            
            return this.valorCarrera = this.precio * this.numeroHoras
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


