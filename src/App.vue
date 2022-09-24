<template>
  <h1>Himagirish Recipe Book</h1>
  <nav-bar />
  <div class="flexbox">
    <div>
      <recipe-comp
      v-for="receipe in receipes"
        :key="receipe.id"
        :name="receipe.name"
        :img="receipe.img"
        :desc="receipe.desc"
        :id="receipe.id"
        @receipeStatus="receipeStatus"/>
    </div>
    <div>
      <show-details
      v-for="receipe in receipes"
        :key="receipe.id"
        :name="receipe.name"
        :img="receipe.img"
        :desc="receipe.desc"
        :id="receipe.id"
        :showRecipe="receipe.showRecipe"/>/>
    </div>
  </div>
</template>

<script>
import RecipeComp from './components/RecipeComp.vue';
import ShowDetails from './components/ShowDetails.vue';


export default {
  name: "App",
  components: {RecipeComp, ShowDetails },
  data() {
    return {
      receipes: [
        {
          id: 1,
          name: "Gulab Jamun",
          desc: "Gulab jamun is a sweet confectionary or dessert, originating in the Indian subcontinent and a type of mithai popular in India, Pakistan, Nepal, the Maldives, and Bangladesh, as well as Myanmar. It is the national dessert of India",
          img: "https://images.unsplash.com/photo-1646578515903-67873a5398f9?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8M3x8Z3VsYWIlMjBqYW11bnxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=500&q=60",
          showRecipe: true,
        },
        {
          id: 2,
          name: "Panner Tikka",
          desc: "Paneer tikka is an Indian dish made from chunks of paneer marinated in spices and grilled in a tandoor. It is a vegetarian alternative to chicken tikka and other meat dishes. It is a popular dish that is widely available in India and countries with an Indian diaspora",
          img: "https://images.unsplash.com/photo-1567188040759-fb8a883dc6d8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1317&q=80",
          showRecipe: true,
        },
        {
          id: 3,
          name: "Puliogre",
          desc: "Pulihora, also known as puliyogare, puliyodarai, pulinchoru, kokum rice, or simply lemon or tamarind rice, is a very common and traditional rice preparation in the South Indian states of Telangana, Andhra Pradesh, Karnataka, Kerala and Tamil Nadu",
          img: "https://rakskitchen.net/wp-content/uploads/2009/03/8546644721_e9a5b7b313_z-500x375.jpg",
          showRecipe: true,
        },
      ],
    };
  },
  methods: {
    receipeStatus(receipeID) {
      console.log("receipeID from child to parent", receipeID);
      let identifiedReceipe = this.receipes.find(
        (receipe) => receipe.id === receipeID
      );
      console.log("identifiedReceipe", identifiedReceipe);
      identifiedReceipe.showRecipe = !identifiedReceipe.showRecipe;
    },
  },
};
</script>

<style>
.flexbox {
  display: flex;
}
h1{
  color: black;
  background-color: green;
}
</style>