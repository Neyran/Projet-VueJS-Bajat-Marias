<template>
    <div>
        <h3>Avis laissés par les consommateurs : </h3>
        <md-table v-model="restaurantInformation.restaurant.grades" md-sort="name" md-sort-order="asc" md-card md-fixed-header>
            <md-table-empty-state
            md-label="No users found"
            :md-description="`No user found for this '${nomRecherche}' query. Try a different search term or create a new user.`">
            </md-table-empty-state>

            

            <md-table-row slot="md-table-row" slot-scope="{ item }">
                <md-table-cell md-label="Date">{{ item.date }}</md-table-cell>
                <md-table-cell md-label="Grade">{{ item.grade }}</md-table-cell>
                <md-table-cell md-label="Score">{{ item.score }}</md-table-cell>
            </md-table-row>
        </md-table>
    </div>
</template>

<script>
export default {
  name: "RestaurantMenu",
  computed: { // computed data, permet de définir des data "calculées"
    id() {
    // on y accèdera par {{id}} dans le template, et par this.id
    // dans le code
    return this.$route.params.id
    },
  },
  props: {},
  data: function() {
    return {
        restaurantInformation: '',
    };
  },
  mounted() {
    console.log("AVANT AFFICHAGE !");
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
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
