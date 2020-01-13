<template>
  <div>

    <div v-if="restaurantInformation.restaurant.address" class="md-layout md-gutter">
      <div class="md-layout-item">
        <h1 style="font: italic small-caps bold 30px cursive;">Consulter Informations</h1>
      </div>
      <div class="md-layout-item" style="margin-top :5em;" >
        <h3>Restaurant : {{restaurantInformation.restaurant.name}}</h3>
      </div>
      <div class="md-layout-item">
        <router-link to="/" style="float: right;"><md-button class="md-raised md-accent">Retour</md-button></router-link>
      </div>
    </div>
        <img v-bind:src="randomPicture()">

        <div v-if="restaurantInformation.restaurant.address" class="md-layout md-gutter">
          <div class="md-layout-item">
            <h3>Adresse : {{restaurantInformation.restaurant.address.building}} {{restaurantInformation.restaurant.address.street}} {{restaurantInformation.restaurant.address.zipcode}} {{restaurantInformation.restaurant.borough}}</h3>
          </div>
          <div class="md-layout-item">
            <h3>Coordonnées GPS : {{restaurantInformation.restaurant.address.coord}} </h3>
          </div>
        </div>

        <RestaurantMenu></RestaurantMenu>

        <RestaurantGrades></RestaurantGrades>
</div>
</template>

<script>

import RestaurantMenu from "@/components/RestaurantMenu.vue";
import RestaurantGrades from "@/components/RestaurantGrades.vue";

export default {
  
  name: "RestaurantDetail",
  components: {
    RestaurantMenu,
    RestaurantGrades,
  },
  props: {},
  computed: { // computed data, permet de définir des data "calculées"
      id() {
        // on y accèdera par {{id}} dans le template, et par this.id
        // dans le code
      return this.$route.params.id
    }
  },
  data: function() {
    return {
      restaurants: [],
      url: '',
      modifyClick: false,
      restaurantInformation: '',
      mainPage: true,
      photos: ['https://www.au-cheval-noir.restaurant/wp-content/uploads/2018/12/Restaurant-Au-Cheval-Noir-Herrlisheim_Photos-8.jpg', 'https://www.hotel-lacloche.fr/sites/hotel-lacloche.fr/files/styles/largeur_2400px/public/2018-12/Restaurant_0.jpg?itok=EPFgF3mj','https://www.lhysope.fr/seize/1800x0/home/carousel/carrousel.jpg','http://www.restaurant-de-la-bourse.fr/wp-content/themes/fso/images/background1.jpg','https://www.marius-pornic.fr/wp-content/uploads/sites/2640/2014/11/marius-restaurant-pornic-67-1000x500.jpg','https://www.felix-restaurant-rennes.com/websites/6f95a1b1114b94f83ea95a6e2bdd5040/img/salle-du-felix-restaurant-rennes_20180924152342.jpg'],  
    };
  },
  mounted() {
    this.getRestaurantInformation(this.id);
  },
  methods: {
    getRestaurantInformation(id){
      fetch("http://localhost:8080/api/restaurants/" + id, {
          method:"GET",
      }).then((reponseJSON => {
          return reponseJSON.json();
      })).then(reponseJS => {
      this.restaurantInformation=reponseJS;
      console.log(this.restaurantInformation);
      })             
    },
    randomPicture(){
      return this.photos[Math.floor(Math.random()*this.photos.length)];
    },
    randomEntree(){
      return this.entrees[Math.floor(Math.random()*this.entrees.length)];
    },
    randomPlat(){
      return this.plats[Math.floor(Math.random()*this.plats.length)];
    },
    randomDessert(){
      return this.dessert[Math.floor(Math.random()*this.dessert.length)];
    }
    
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
