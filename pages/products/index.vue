<template>
    <div> 
 
    
        <h2> Our Products </h2>
        <div> 
            <label>Search</label>
        <input v-model="search" type="text" placeholder="Type your text here">
        <select v-model="category">
        <option value="any">Any</option>
        <option value="men's clothing">Men's Clothing</option>
        <option value="jewelery">Jewelery</option>
      </select>

        </div>
        
        <ul>
            <li v-for="product in filtered" :key="product.id">
                <div> 
                    <ProductCard :product="product"/>
                    

                </div>
            </li>
        </ul>

    </div>

    
</template>

<script>
import ProductCard from './components/ProductCard.vue';


export default {
    layout: 'Product',
    data(){
        return {
            products: [],
            search:"",
            category:"",
        };
    },
    components:{
        ProductCard

    },

    async mounted(){
        const res = await fetch("https://fakestoreapi.com/products");
        const data = await res.json();
        this.products = data;

    },
    computed:{
        filtered(){
            if (!this.search && this.category ==="any"){
                return this.products;
            }
        
            return this.products.filter(product => {
            const matchtitle= product.title.toLowerCase().includes(this.search.toLocaleLowerCase());
            const matchCategory = product.category === this.category;
            return matchtitle&&matchCategory;

        })
    }
},
}

</script>

<style scoped> 
</style>