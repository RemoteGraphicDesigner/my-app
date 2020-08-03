<template>
    <div>
         <ul v-bind:key="ingredient" v-for="ingredient in ingredients" class="list-group list-group-flush">
            <li class="list-group-item">{{ingredient}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "IngredientsCocktail.vue",
    props: {
        "ingredients": Array
    }
}
</script>

<style scoped>

</style>