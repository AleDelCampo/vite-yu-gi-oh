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
        {{ card.name }} <br> <span>{{ card.archetype }}</span>
    </li>

</template>


<style lang="scss">

.card-container {
    display: flex;
    flex-direction: column;
    text-align: center;
    width: calc(100% / 5 - 20px / 5 * 4);
    background-color: #d48f38;

    span {
        color: red;
    }
}
</style>