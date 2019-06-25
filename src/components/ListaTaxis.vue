<template>
    <div class="container">
        <div class="row">
            <div class="col-md-12">
                <div @click="cambiarEstado(id)" 
                    :class="['alert', item.estado ? 'alert-primary' : 'alert-danger']"
                    role="alert"
                    v-for="(item, id) of taxis" :key="item.id">
                    <b>{{item.placa}}</b>
                </div>
            </div>
        </div>
        
    </div>
</template>
<script>
export default {
    name:'ListaTaxis',
    data() {
        return {
            taxis:[
                {placa:'XAS-123', marca:'NISSAN',estado:true},
                {placa:'XAS-124', marca:'TOYOTA',estado:false},
                {placa:'XAS-125', marca:'SI',estado:true},
            ],
        }
    },
    methods: {
        cambiarEstado(id){
            if(this.taxis[id].estado){
                this.taxis[id].estado=false
            }else{
                this.taxis[id].estado=true
            }
        },
       
    }
}
</script>