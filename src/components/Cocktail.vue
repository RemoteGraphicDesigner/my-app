<template>
    <div class="card">
        <div v-bind:key="cocktail.id" v-for="cocktail in cocktails">
                <IngredientsCocktail v-bind:ingredients="test(getMessurements(cocktail), getIngredients(cocktail))"/>
            <div class="card-body">
                <a href="https://www.drink.ch/de/" class="card-link">Buy</a>
                <a v-bind:href="'https://www.google.com/search?q=' + cocktail.strDrink" class="card-link">Search Google</a>
            </div>
        </div>
    </div>
</template>

<script>import IngredientsCocktail from "./CocktailComponents/IngredientsCocktail";

export default {
    name: "Cocktail",
    props: ["cocktails"],
    components: {
        IngredientsCocktail
    },
    methods: {
        getIngredients(cocktail) {
            var array = [cocktail.strIngredient1, cocktail.strIngredient2, cocktail.strIngredient3, cocktail.strIngredient4, cocktail.strIngredient5, cocktail.strIngredient6, 
            cocktail.strIngredient7, cocktail.strIngredient8, cocktail.strIngredient9, cocktail.strIngredient10, cocktail.strIngredient11, cocktail.strIngredient12,
            cocktail.strIngredient13, cocktail.strIngredient14]

            return array.filter(Boolean);
        },
        getMessurements(cocktail){
            var array = [cocktail.strMeasure1, cocktail.strMeasure2, cocktail.strMeasure3, cocktail.strMeasure4, cocktail.strMeasure5, cocktail.strMeasure6, 
            cocktail.strMeasure7, cocktail.strMeasure8, cocktail.strMeasure9, cocktail.strMeasure10, cocktail.strMeasure11, cocktail.strMeasure12,
            cocktail.strMeasure13, cocktail.strMeasure14]

            return array.filter(Boolean);
        },
        test(measurements,ingredients){
            for(var i = 0; i < ingredients.length; i++){
                ingredients[i] += " " + measurements[i];
            }
            return ingredients;
        }
    }
}
</script>

<style scoped>
    .card{
        min-width: 250px;
        margin-top: 2em;
    }
</style>