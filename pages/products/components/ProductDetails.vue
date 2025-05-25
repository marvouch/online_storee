<template>
    <div class="l">
        <div> 
             <img :src="product.image" width="40" height="100">
        </div>

        <div class="d"> 
           <p> {{ product.tile }}</p>
           <p> {{ product.price }} MAD</p>
           <p> {{ product.description }}</p>
           <p>{{ product.category }}</p>
           

        </div>
    </div>
    
</template>

<script>
export default{
    props:{
        product:{
            type:Object,
            required:true,
        }
    }
}
</script>
<style scoped> 
.d{
    display: flex;
    flex-direction: column;
}
.l{
    display:flex;
    flex-direction : row;
}
</style>