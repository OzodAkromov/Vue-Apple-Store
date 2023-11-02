<template>
    <div class="card">
        <img :src="productInfo.image" alt="#">

        <h3>{{ productInfo.name }}</h3>

        <button @click="$emit('action')">Read More</button>
    </div>
</template>

<script>
export default {
    props: {
        productInfo:{
            type: [Object, String],
            required: true
        }
    }
}
</script>

<style lang="scss">
.card {
    width: 250px;
    padding: 15px;
    border-radius: 10px;
    box-shadow: 0 0 10px grey;

    img {
        width: 100%;
        height: 250px;
        object-fit: cover;
        border-radius: 10px;
    }

    h3 {
        text-align: center;
        font-size: 21px;
        margin: 10px 0;
    }

    button {
        background: dodgerblue;
        color: white;
        padding: 12px 20px;
        border-radius: 10px;
        display: block;
        margin-left: auto;
        margin-top: 25px;
    }
}
</style>