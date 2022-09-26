<template><div class="row">
    <div class="col-lg-8">
        <h4>{{titulo}}</h4>
        <table class="table">
            <thead>
                <tr>
                    <th>N:</th>
                    <th>Modelo</th>
                    <th>Descripcion</th>
                    <th>Price</th>
                    <th>Porcentaje de descuento</th>
                </tr>
            </thead>

            <tbody>
                <tr v-for="(u,index) of lista_productos" v-bind:key="index">
                    <td>{{index}}</td>
                    <td>{{u.title}}</td>
                    <td>{{u.description}}</td>
                    <td>{{u.price}}</td>
                    <td>{{u.discountPercentage}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</div>
</template>
<script>
/* eslint-disable */
import { ref } from 'vue'
export default {
    name:'FormProdcuto',
    setup() {    
        //sector de variables
        let lista_usuarios = ref([])
        let titulo = ref('Lista de Prodcutos')

        //sector de funciones
        async function consumir_api2(){
            const productos = await fetch('https://dummyjson.com/products')
            lista_productos.value = await productos.json()            
        }

        return{
            consumir_api2,
            lista_productos,
            titulo
        }
    },
}
</script>