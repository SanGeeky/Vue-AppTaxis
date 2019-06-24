<template>
    <div class="container">
        <div class="row">
            <h4>Lista du Taxis</h4>
            <div class="col-md-12">
                <div role="alert" 
                v-for="(item, id) of taxis" :key="item.id"
                :class="['alert', item.estado ? 'alert-primary':'alert-danger']"
                v-on:click="ActualizarEstado(id)">
                <b>{{ item.placa }} - {{ item.marca }} - {{ item.estado}}</b>
                </div>
                            <!-- <ul v-for="item of taxis" :key="item.id" class="list-group">
                        <li class="list-group-item"> </li> -->
                </ul>
            </div>
        </div>
    </div>
</template>


<script>
export default {
    name:'Taxis',
    data (){
        return{
            taxis:[
                {placa:'SXA-987', marca: 'Nissan', estado:true},
                {placa:'CPB-353', marca: 'Chevrolet', estado:false},
                {placa:'NPA-934', marca: 'Toyota', estado:true}
            ]
                           
        }
    },
    methods:{
        ActualizarEstado(index){
            if(this.taxis[index].estado)
                this.taxis[index].estado=false;
            else
                this.taxis[index].estado=true;                
        }

    }
    

    
}

</script>
