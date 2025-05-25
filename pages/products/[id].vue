<template>
    <div>
        
            <div v-for="product in products" :key="product.id">
                <div v-if="id == product.id"> 
                    <ProductDetails :product="product"/>
                    

                </div>
            
            </div>

    </div>

    
</template>

<script>
import ProductDetails from './components/ProductDetails.vue';


export default {
    data(){
        return {
            products: [],
            id:null,
        };
    },
    components:{
        ProductDetails

    },

    async mounted(){
        
        this.id = Number(this.$route.params.id);
        const res = await fetch("https://fakestoreapi.com/products");
        const data = await res.json();
        this.products = data;
       

    },
   
};

</script>

<style scoped> 
</style>