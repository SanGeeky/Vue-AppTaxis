<template>
    <div class="container">
        <div class="row">
            <h4>Lista du Taxis</h4>
            <div class="col-md-12">
                <ul v-for="item of taxis" :key="item.id" class="list-group">
                <li class="list-group-item">{{ item.placa }} - {{ item.marca }} - {{ item.estado}} </li>
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
                {placa:'CPB-353', marca: 'Chevrolet', estado:true},
                {placa:'NPA-934', marca: 'Toyota', estado:true}
            ]
               
        }
    }
}

</script>
