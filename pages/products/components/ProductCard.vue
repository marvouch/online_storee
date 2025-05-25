
<template>
    <div class="div">

        <img :src="product.image" width="40" height="70">
        {{ product.title }}
        <NuxtLink :to="`/products/${product.id}`" class="button">View details</NuxtLink>

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
.button{
    background-color:green;
    padding: 20px;
    margin : 10px;
    width: 60px;
}
.div{
    background-color: burlywood;
    display: flex;
    flex-direction: column;
    margin:20px;

}
</style>
