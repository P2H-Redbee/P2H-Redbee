<template>
    <div class="home">
        <a href="#"><img :src="원룸.image" alt="없어" /></a>
        <h1 @click="$emit('openModal', 원룸.id)">{{ 원룸.title }}</h1>
        <p>{{ 원룸.price }}원</p>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: {
        원룸: Object,
    },
};
</script>

<style>
.home {
    margin-top: 30px;
}
img {
    width: 100%;
}
div {
    box-sizing: border-box;
}
</style>
