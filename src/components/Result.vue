<template>
    <p class="score">Reaction Time : {{ score }}</p>
</template>
<script>
export default {
    name: "Result",
    props: ['score'],
}
</script>
<style>
.score {
    margin-top: 1rem;
    font-weight: 500;
    font-size: 20px;
}
</style>