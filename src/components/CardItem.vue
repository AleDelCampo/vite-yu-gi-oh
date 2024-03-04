<script>

export default {
    
    name: 'CardItem',
    
    props: {
        card: Object,
    },
}

</script>

<template>

    <li class="card-container">
        <img v-for="image in card.card_images" :src="image.image_url" >
        {{ card.name }}
    </li>

</template>

<style lang="scss">

.card-container {
    display: flex;
    flex-direction: column;
    text-align: center;
    width: calc(100% / 3 - 20px / 3 * 2);
}

</style>