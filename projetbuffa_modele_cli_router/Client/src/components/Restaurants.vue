<template>
<div>
  <md-field>
      <label>Rechercher par nom:</label>
      <md-input type="text" v-model="nomRecherche" v-on:input="getDataFromServer()" />
  </md-field>
  
  <div class="md-layout md-gutter">
    <div class="md-layout-item">
      <p>
      Nombre de restaurants par page :
      <input
      type="range"
      min="2"
      max="100"
      value="10"
      v-on:input="getDataFromServer()"
      v-model="pagesize"
      />
      {{pagesize}}
      </p>
      <button v-on:click="pagePrecedente()" v-bind:disabled="page==0">Précédent</button>
      <button v-on:click="pageSuivante()" :disabled="page == nbPagesDeResultats">Suivant</button>
    </div>
    
    <div class="md-layout-item">
      <h1>Nombre de restaurants total: {{nbRestaurants}}</h1>
    </div>

  </div>

  
  
 
  <H1>Liste des restaurants</H1>
        <md-table v-model="restaurants" md-sort="name" md-sort-order="asc" md-card md-fixed-header>
            <md-table-toolbar>
                <div class="md-toolbar-section-start">
                    <h1 class="md-title">Nom cherche</h1>
                </div>

                <md-field md-clearable class="md-toolbar-section-end">
                    <md-input placeholder="Search by name..." v-model="nomRecherche" @input="getDataFromServer()" />
                </md-field>
            </md-table-toolbar>

            <md-table-empty-state
        md-label="No users found"
        :md-description="`No user found for this '${nomRecherche}' query. Try a different search term or create a new user.`">
      </md-table-empty-state>

            

            <md-table-row slot="md-table-row" slot-scope="{ item }">
                <md-table-cell md-label="Name" md-sort-by="name">{{ item.name }}</md-table-cell>
                <md-table-cell md-label="Cuisine" md-sort-by="cuisine">{{ item.cuisine }}</md-table-cell>
                <md-table-cell md-label="Details"><md-button><router-link :to="'restaurant/'+item._id">Details</router-link></md-button>
                <md-button class="md-raised md-primary" v-on:click="supprimerRestaurant(item._id)">Supprimer</md-button>
                <md-button class="md-raised md-primary" v-on:click="setModifyTrue(item._id,item.name,item.cuisine)">Modifier</md-button></md-table-cell>
            </md-table-row>
        </md-table>

  <form v-on:submit="modifierRestaurant" v-if="modifyClick">
      <br>
      <br>
      <div class="md-layout md-gutter">
        <div class="md-layout-item">
          <md-field>
            <label>Id :</label>
            <md-input type="text" v-model="nomRecherche" v-on:input="getDataFromServer()" />
          </md-field>
        </div>
        <div class="md-layout-item">
          <md-field>
            <label>Nom :</label>
            <md-input type="text" v-model="nomRecherche" v-on:input="getDataFromServer()" />
          </md-field>
        </div>
        <div class="md-layout-item">
          <md-field>
            <label>Cuisine :</label>
            <md-input type="text" v-model="nomRecherche" v-on:input="getDataFromServer()" />
            </md-field>
        </div>
        <div class="md-layout-item">
            <md-button class="md-raised md-primary">Modifier</md-button>
        </div>
      </div>
  </form>
</div>
</template>

<script>
export default {
  name: "Restaurants",
  props: {},
  data: function() {
    return {
      restaurants: [],
      nbRestaurants: 0,
      nom: "",
      cuisine: "",
      page: 0,
      pagesize: 10,
      nomRecherche: "",
      nbPagesDeResultats: 0,
      apiURL: "http://localhost:8080/api/restaurants",
      id_modify: '',
      nom_modify: '',
      cuisine_modify: '',
      modifyClick: false,
    };
  },
  mounted() {
    console.log("AVANT AFFICHAGE !");
    this.getDataFromServer();
  },
  methods: {
    getDataFromServer() {
      // ici on fait un fetch pour récupérer des
      // restaurants sur le serveur.
      let url =
        this.apiURL +
        "?page=" +
        this.page +
        "&pagesize=" +
        this.pagesize +
        "&name=" +
        this.nomRecherche;

      fetch(url)
        .then(reponseJSON => {
          return reponseJSON.json();
        })
        .then(reponseJS => {
          // ici on a la réponse sous la forme
          // d'un objet JS
          this.restaurants = reponseJS.data;
          this.nbRestaurants = reponseJS.count;
          this.nbPagesDeResultats = Math.floor(
          this.nbRestaurants / this.pagesize
          );
        });
    },
    supprimerRestaurant(id) {
      //this.restaurants.splice(index, 1);
      fetch("http://localhost:8080/api/restaurants/" + id,
      {
          method:"DELETE"
      }).then((reponseJSON => {
          return reponseJSON.json();
      })).then(reponseJS => {
          this.getDataFromServer();
          console.log(reponseJS);
      })
    },
    ajouterRestaurant(event) {
      // eviter le comportement par defaut
      event.preventDefault();

      this.restaurants.push({
        nom: this.nom,
        cuisine: this.cuisine
      });
      this.nom = "";
      this.cuisine = "";
    },
    modifierRestaurant(event) {
      // eviter le comportement par defaut
      event.preventDefault();

      let form = new FormData();
      form.append("id", this.id_modify)
      form.append("nom", this.nom_modify);
      form.append("cuisine", this.cuisine_modify);

      fetch("http://localhost:8080/api/restaurants/" + this.id_modify, {
          method:"PUT",
          body:form
      }).then((reponseJSON => {
          return reponseJSON.json();
      })).then(reponseJS => {
          this.getDataFromServer();
          console.log(reponseJS);

      })                

      this.modifyClick = false;
    },
    getColor(index) {
      return index % 2 ? "lightBlue" : "pink";
    },
    pageSuivante() {
      console.log("Page suivante");
      this.page++;
      this.getDataFromServer();
    },
    pagePrecedente() {
      console.log("Page precedente");
      this.page--;
      this.getDataFromServer();
    },
    setModifyTrue(id,nom,cuisine){
        this.modifyClick = true;
        this.id_modify = id;
        this.nom_modify = nom;
        this.cuisine_modify = cuisine;
    },
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
