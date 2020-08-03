<template>
  <div id="app">
    <header class="overlay">
      <h1> Cocktail Recipes </h1>
    </header>
    <main id="cocktailApp">
        <div class="search-box">
          <input 
            type="text" 
            class="search-bar" 
            placeholder="Search..." 
            v-model="query"
            @keypress="fetchCocktail"
          />
        </div>

        <section class="cards" dv-if="drinks.main !='undefined'">
          <article class="card" v-for="drink in drinks.drinks" v-bind:key="drink.idDrink">

            <picture class="thumbnail">
              <img :src="drink.strDrinkThumb" alt="" />
            </picture>

            <div class="card-content" id ="cocktail-card">
              <button class="name" @click="show = !show">
                {{ drink.strDrink }}
              </button>
              <div>
                  <p class="alternative"> {{ drink.strDrinkAlternate }} </p>
                  <p class="category">  {{ drink.strCategory }} </p>
                  <Cocktail v-bind:cocktails="drinks.drinks" />
                  <!-- <table class="ingredients">
                    <tr>
                      <td> {{ drink.strMeasure1 }} </td>
                      <td> {{ drink.strIngredient1 }} </td>
                    </tr>
                  </table> -->
                  <!-- <IngredientsCocktail v-bind:ingredients="test(getMessurements(cocktail), getIngredients(cocktail))"/> -->
                  <p class="instructions"> {{ drink.strInstructions }} </p>
                </div>

            </div> <!-- .card-content -->

          </article>
        </section>

    </main>

  </div>
</template>


<script>
import Cocktail from "./components/Cocktail";
export default {
  name: 'App',
  comonents:{
    Cocktail
  },
  el: '#cocktailApp',
  data () {
    return{
      url_base: 'https://www.thecocktaildb.com/api/json/v1/1/',
      query: '',
      drinks: {},
      ingredients:[],
      measurements:[]
    }
  },
  methods: {
    fetchCocktail (e) {
      if (e.key =="Enter"){
        fetch(`${this.url_base}search.php?s=${this.query}`)
          .then(res => {
            return res.json();
          }).then(this.setResults);
      }
    },
    setResults (results) {
      this.drinks = results;
    },
    ingredientTable(tbody){
      var tr, td;
      tbody = matchData.querySelector('tbody');
      for (var i=1; i<16; i++){
        tr = tbody.insertRow(tbody.rows.length);
        td = tr
      }
    }
  }
}
// import Vue from 'vue'

// new Vue({
//   el: '#cocktail-card',
//   data: {
//     show: true
//   }
// })
</script>

<style>

@import "./assets/style.css";
</style>
