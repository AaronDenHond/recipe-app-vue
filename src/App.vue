<template>
  <!-- submit.prevent wont reload the page -->
  <form @submit.prevent="addRecipe">
    <div>
      <label>Name</label><br />
      <!-- v-model is vue's way of 2way binding input data to model -->
      <input v-model="recipe.name" type="text" name="" id="" />
    </div>
    <div>
      <label>Ingredients</label><br />
      <textarea
        v-model="recipe.ingredients"
        name=""
        id=""
        cols="30"
        rows="5"
      ></textarea>
    </div>
    <div>
      <label>Instructions</label><br />
      <textarea
        v-model="recipe.instructions"
        name=""
        id=""
        cols="30"
        rows="10"
      ></textarea>
    </div>
    <button type="submit">Add Recipe</button>
  </form>
  <!-- v-for is vues way of foreach loping -->
  <div v-for="recipe of recipes" v-bind:key="recipe.id">
    <h1>Name</h1>
    <p>{{ recipe.name }}</p>
    <h1>Ingredients</h1>
    <p>{{ recipe.ingredients }}</p>
    <h1>Instructions</h1>
    <p>{{ recipe.instructions }}</p>
    <button @click="deleteRecipe">Delete Recipe</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      recipe: {
        name: "",
        ingredients: "",
        instructions: "",
      },
      recipes: [],
    };
  },
  methods: {
    addRecipe() {
      this.recipes.push(this.recipe);
      console.log(this.recipes);
    },
    deleteRecipe(start){
      this.recipes.splice(start,1)
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
