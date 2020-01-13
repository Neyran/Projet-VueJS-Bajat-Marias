<template>
    <div>
        <h1 style="margin-top : 3em;">Nos menus</h1>

        <div class="md-layout md-gutter">
            <div class="md-layout-item">
                <md-card md-with-hover>
                    <md-ripple>
                        <md-card-header>
                        <div class="md-title">{{menu[0].nom}}</div>
                        <div class="md-subhead">{{menu[0].prix}}</div>
                        </md-card-header>
                        
                        <md-card-content>
                            <h3>Entrée</h3>
                            <p>{{menu[0].entree.nom}} {{menu[0].entree.ingrédient}}</p>
                            <img v-bind:src="menu[0].entree.photo">
                            <h3>Plat</h3>
                            <p>{{menu[0].plat.nom}} {{menu[0].plat.ingrédient}}</p>
                            <img v-bind:src="menu[0].plat.photo">
                            <h3>Dessert</h3>
                            <p>{{menu[0].dessert.nom}} {{menu[0].dessert.ingrédient}}</p>
                            <img v-bind:src="menu[0].dessert.photo">
                        </md-card-content>
                    </md-ripple>
                </md-card>            
            </div>
            <div class="md-layout-item">
                <md-card md-with-hover>
                    <md-ripple>
                        <md-card-header>
                        <div class="md-title">{{menu[1].nom}}</div>
                        <div class="md-subhead">{{menu[1].prix}}</div>
                        </md-card-header>
                        
                        <md-card-content>
                            <h3>Entrée</h3>
                            <p>{{menu[1].entree.nom}} {{menu[1].entree.ingrédient}}</p>
                            <img v-bind:src="menu[1].entree.photo">
                            <h3>Plat</h3>
                            <p>{{menu[1].plat.nom}} {{menu[1].plat.ingrédient}}</p>
                            <img v-bind:src="menu[1].plat.photo">
                            <h3>Dessert</h3>
                            <p>{{menu[1].dessert.nom}} {{menu[1].dessert.ingrédient}}</p>
                            <img v-bind:src="menu[1].dessert.photo">             
                        </md-card-content>
                    </md-ripple>
                </md-card>
            </div>
            <div class="md-layout-item">
                <md-card md-with-hover>
                    <md-ripple>
                        <md-card-header>
                        <div class="md-title">{{menu[2].nom}}</div>
                        <div class="md-subhead">{{menu[2].prix}}</div>
                        </md-card-header>
                        
                        <md-card-content>
                            <h3>Entrée</h3>
                            <p>{{menu[2].entree.nom}} {{menu[2].entree.ingrédient}}</p>
                            <img v-bind:src="menu[2].entree.photo">
                            <h3>Plat</h3>
                            <p>{{menu[2].plat.nom}} {{menu[2].plat.ingrédient}}</p>
                            <img v-bind:src="menu[2].plat.photo">
                            <h3>Dessert</h3>
                            <p>{{menu[2].dessert.nom}} {{menu[2].dessert.ingrédient}}</p>
                            <img v-bind:src="menu[2].dessert.photo">
                        </md-card-content>
                    </md-ripple>
                </md-card>
            </div>
        </div>
                    
        <h1 style="margin-top : 3em;">A la carte</h1>
        <div class="md-layout md-gutter">
            <div class="md-layout-item">
                <md-list class="md-double-line">
                    <md-subheader>Entrées</md-subheader>
                    <md-list-item v-for="item in entrees" :key='item'>
                        <div class="md-list-item-text">
                            <span>{{item.nom}} {{item.prix}} </span>
                            <span>{{item.ingrédient}}</span>
                        </div>
                        <md-divider></md-divider>
                    </md-list-item>
                </md-list>
            </div>
            <div class="md-layout-item">
                <md-list class="md-double-line">
                    <md-subheader>Plats</md-subheader>

                    <md-list-item v-for="item in plats" :key='item'>
                        <div class="md-list-item-text">
                            <span>{{item.nom}} {{item.prix}} </span>
                            <span>{{item.ingrédient}}</span>
                        </div>
                    </md-list-item>
                </md-list>
            </div>
            <div class="md-layout-item">
                <md-list class="md-double-line">
                    <md-subheader>Desserts</md-subheader>

                    <md-list-item v-for="item in desserts" :key='item'>
                        <div class="md-list-item-text">
                            <span>{{item.nom}} {{item.prix}} </span>
                            <span>{{item.ingrédient}}</span>
                        </div>
                    </md-list-item>
                </md-list>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: "RestaurantMenu",
  props: {},
  data: function() {
    return {
    dessert: "",
    plat: "",
    entree: "",
    menu : [],
       photos: ['https://www.au-cheval-noir.restaurant/wp-content/uploads/2018/12/Restaurant-Au-Cheval-Noir-Herrlisheim_Photos-8.jpg', 'https://www.hotel-lacloche.fr/sites/hotel-lacloche.fr/files/styles/largeur_2400px/public/2018-12/Restaurant_0.jpg?itok=EPFgF3mj','https://www.lhysope.fr/seize/1800x0/home/carousel/carrousel.jpg','http://www.restaurant-de-la-bourse.fr/wp-content/themes/fso/images/background1.jpg','https://www.marius-pornic.fr/wp-content/uploads/sites/2640/2014/11/marius-restaurant-pornic-67-1000x500.jpg','https://www.felix-restaurant-rennes.com/websites/6f95a1b1114b94f83ea95a6e2bdd5040/img/salle-du-felix-restaurant-rennes_20180924152342.jpg'],
            entrees: [{
                nom :'Salade de chèvre chaud',
                photo : "https://assets.afcdn.com/recipe/20160426/5347_w420h344c1cx1920cy2880.jpg",
                prix : "15€",
                ingrédient :["Chèvre","Pain","Salade","Tomates"]},
                {
                nom : 'Soupe aux légumes verts',
                photo : "https://static.hervecuisine.com/wp-content/uploads/2016/09/recette-soupe-detox-768x512.jpg",
                prix : "25€",
                ingrédient : ["Courgettes","Poireau","fenouil","ail"]},
                {
                nom : 'Soupe aux champignons',
                photo : "https://assets.afcdn.com/recipe/20160404/36766_w420h344c1cx1500cy1288.jpg",
                prix : "25€",
                ingrédient : ["Champignons de Paris","oignon","ail","Poivre","Sel"]},
                {
                nom : "Tartare de saumon et d'avocat",
                photo : "https://assets.afcdn.com/recipe/20160404/544_w420h344c1cx1574cy2376.jpg",
                prix : "30€",
                ingrédient : ["Avocat","échalote","Citron","Saumon fumé"]},
                {
                nom : "Tartine de saumon fumé au fromage frais",
                photo : "https://www.papillesetpupilles.fr/wp-content/uploads/2012/12/Tartines-du-dimanche-soir-au-Kiri-et-au-saumon-fum%C3%A9-500x0.jpg",
                prix : "20€",
                ingrédient : ["Pain croustillant","Citron","Jambon fumé","roquette"]},
                {
                nom : "Avocat aux crevettes",
                photo : "https://assets.afcdn.com/recipe/20131009/48144_w420h344c1cx3392cy2456.jpg",
                prix : "15€",
                ingrédient : ["Avocat","crevette","Poivre","Oeuf"]},
                {
                nom : "Mini quiches aux asperges et tomates",
                photo : "https://static.cuisineaz.com/240x192/i113549-mini-quiche-aux-tomates-cerises-et-asperge.jpg",
                prix : "20€",
                ingrédient : ["Asperges","Tomate","pâte brisée"]},
                {
                nom : "Salade de betterave",
                photo : "https://assets.afcdn.com/recipe/20100120/9861_w420h344c1cx256cy192.jpg",
                prix : "20€",
                ingrédient : ["Salade","Betterave","Persil"]},
                {
                nom : "Bricks à la viande",
                photo : "https://assets.afcdn.com/recipe/20170602/43452_w420h344c1cx3008cy2008.jpg",
                prix : "15€",
                ingrédient : ["Persil","sel","Poivre","Viande hachée"]},
               {
                nom : "Chaussons aux légumes",
                photo : "https://static.750g.com/images/622-auto/ba87a529a3e16906d359deba3b9be553/chaussons-aux-legumes-maison.jpeg",
                prix : "15€",
                ingrédient : ["Courgettes","oignon","Poivron","Huile d'olive"]}],

             plats : [{
            nom : "Filet mignon en croûte", 
            photo : "https://assets.afcdn.com/recipe/20160405/35684_w420h344c1cx1500cy1000.jpg",
            prix : "25€",
            ingrédient : ["filet mignon","Moutarde","Poivre","Oeuf"]},
            {
            nom : "Lasagnes à la bolognaise",
            photo : "https://assets.afcdn.com/recipe/20160630/63224_w420h344c1cx1500cy2248.jpg",
            prix : "25€",
            ingrédient : ["Gousse d'ail","Oignon","pâte de lasagne"]},
            {
            nom : "Boeuf Bourguignon rapide",
            photo : "https://assets.afcdn.com/recipe/20131009/56293_w420h344c1cx1872cy2808.jpg", 
            prix : "20€",
            ingrédient : ["Lardon","Oignon","Bouqet garni"]},
            {
            nom : "Amour de saumon en papillote",
            photo : "https://assets.afcdn.com/recipe/20150922/57763_w420h344c1cx1296cy864.jpg",
            prix : "24€",
            ingrédient : ["Saumons frais","Ail","Tomate cerise","Citron"]},
            {
            nom : "Endive jambon",
            photo : "https://assets.afcdn.com/recipe/20180621/79730_w420h344c1cx1944cy2592cxt0cyt0cxb3888cyb5184.jpg", 
            prix : "25€",
            ingrédient : ["Endive","Jambon","Frommage"]},
            {
            nom : "Filet mignon de porc au Maroilles",
            photo : "https://assets.afcdn.com/recipe/20130304/1669_w420h344c1cx1000cy1312.jpg", 
            prix : "25€",
            ingrédient : ["Porc","Pâte","Maroilles"]},
            {
            nom : "Gratin Dauphinois",
            photo : "https://assets.afcdn.com/recipe/20160401/5313_w420h344c1cx2088cy1412.jpg", 
            prix : "35€",
            ingrédient : ["Pomme de terre","Crème","Lait"]},
            {
            nom : "Couscous poulet et merguez",
            photo : "https://assets.afcdn.com/recipe/20180621/79724_w420h344c1cx1944cy2592cxt0cyt0cxb3888cyb5184.jpg", 
            prix : "25€",
            ingrédient : ["Merguez","Poulet","Huile d'olive","Harissa"]},
            {
            nom : "Poulet basquaise",
            photo : "https://assets.afcdn.com/recipe/20170614/69328_w420h344c1cx2000cy3000.jpg", 
            prix : "25€",
            ingrédient : ["Poulet","Tomate","Ail"]},
            {
            nom : "Sauté de veau au chorizo",
            photo : "https://assets.afcdn.com/recipe/20130122/35196_w420h344c1cx192cy256.jpg",
            prix : "25€",
            ingrédient : ["Veau","Chorizo","Tomates"]},
            {
            nom : "Lapin à la moutarde",
            photo : "https://assets.afcdn.com/recipe/20180628/80080_w420h344c1cx1818cy2361cxt0cyt0cxb3637cyb4723.jpg",
            prix : "35€",
            ingrédient : ["Lapin","Moutarde","Persil","Citron"]}
            //"Filet mignon en croûte","Lasagnes à la bolognaise","","Hachis Parmentier","Boeuf Bourguignon rapide","","Poulet à la moutarde, à l'estragon et aux champignons","Filet mignon de porc au Maroilles","Chili con carne","Endive jambon","Couscous poulet et merguez","","Quiche lorraine","Tarte tatin de légumes"," maison","Poulet basquaise","Carbonades flamandes traditionnelles","Boeuf braisé aux carottes","Crevettes au curry","Rôti de porc de Dijon","Ratatouille","Parmentier de confit de canard","Tajine d'agneau aux pruneaux","Pâte à pizza fine","Tartiflette","Riz au curry et crevettes","Spaghetti alla carbonara","Pâtes au saumon fumé","Bruschetta tomates mozzarella","Poulet au curry coco","Crevettes à l'indienne","Quiche aux poireaux"],
             ],
            desserts : [{
                nom :"Tarte chocolat poire",
                photo :"https://assets.afcdn.com/recipe/20161010/63134_w420h344c1cx2592cy1728.jpg",
                prix : "15€",
                ingrédient : ["Poire","Pâte Feuilletés","Chocolat Noir"]},
                {
                nom : "Tarte au citron meringuée",
                photo :"https://assets.afcdn.com/recipe/20170213/63346_w420h344c1cx3000cy2000.jpg",
                prix : "10€",
                ingrédient : ["citron","Oeuf","Sucre"]},
                 {
                nom :"Verrines de framboises",
                photo :"https://assets.afcdn.com/recipe/20130415/8839_w420h344c1cx256cy192.jpg",
                prix : "20€",
                ingrédient : ["Framboises","Oeufs","Mascarpone"]},
                 {
                nom :"Tarte aux pommes",
                photo :"https://assets.afcdn.com/recipe/20180705/80308_w420h344c1cx1944cy2592cxt0cyt0cxb3888cyb5184.jpg",
                prix : "13€",
                ingrédient : ["Pâte brisée","Pommes","Sucre vanillé"]},
                 {
                nom :"Cake aux pépites de chocolat",
                photo :"https://assets.afcdn.com/recipe/20140614/60653_w420h344c1cx1632cy918.jpg",
                prix : "14€",
                ingrédient : ["Levure","Chocolat Noir","Sucre glace"]},
                 {
                nom :"Crème au chocolat",
                photo :"https://assets.afcdn.com/recipe/20160520/48635_w420h344c1cx1950cy2925.jpg",
                prix : "15€",
                ingrédient : "Chocolat noir"},
                 {
                nom :"Gâteau moelleux aux pêches",
                photo :"https://cac.img.pmdstatic.net/fit/http.3A.2F.2Fprd2-bone-image.2Es3-website-eu-west-1.2Eamazonaws.2Ecom.2Fcac.2F2018.2F09.2F25.2F202d66c2-a22b-4213-a560-9bf89f7b7a8c.2Ejpeg/748x372/quality/90/crop-from/center/gateau-moelleux-aux-peches.jpeg",
                prix : "17€",
                ingrédient : ["Pêches","Pâte brisée"]},
                 {
                nom :"Tarte tatin aux pommes",
                photo :"https://assets.afcdn.com/recipe/20180503/79001_w420h344c1cx2880cy1920.jpg",
                prix : "16€",
                ingrédient : ["Pommes","Levure","Pâte brisée"]},
                 {
                nom :"Crumble aux pommes",
                photo :"https://assets.afcdn.com/recipe/20130823/26376_w420h344c1cx1728cy2424.jpg",
                prix : "17€",
                ingrédient : ["Pommes","glace vanille"]},
                 {
                nom :"Madeleines",
                photo :"https://assets.afcdn.com/recipe/20161128/3468_w420h344c1cx2617cy1782.jpg",
                prix : "14€",
                ingrédient : "Levure chimique"},
                 {
                nom :"Quatre-quarts maison",
                photo :"https://assets.afcdn.com/recipe/20170905/71712_w420h344c1cx2000cy3000cxt0cyt0cxb4000cyb6000.jpg",
                prix : "20€",
                ingrédient : ["Sucre vanillé","Levure Chimique"]}   
            ],

            menus : [{
                nom : "Gastronomique",
                prix : "75€",
                entree : "",
                plat : "",
                dessert : ""},
                {
                nom : "Economique",
                prix :"25€",
                entree : "",
                plat: "",
                dessert : ""},
                {
                nom : "Enfant",
                prix : "30€",
                entree : "",
                plat : "",
                dessert : ""},
                {
                nom : "Provencal",
                prix : "55€",
                entree : "",
                plat: "",
                dessert : ""},
                {
                nom : "Italien",
                prix : "48€",
                entree : "",
                plat : "",
                dessert : ""},
                {
                nom : "Boucher",
                prix : "50€",
                entree : "",
                plat : "",
                dessert : ""},
                {
                nom : "Végétarien",
                prix : "35€",
                entree : "",
                plat : "",
                dessert : ""},
                {
                nom : "Vegan",
                prix : "30€",
                entree : "",
                plat : "",
                dessert : ""},
                {
                nom : "Oriental",
                prix : "40€",
                entree : "",
                plat : "",
                deseert : ""},
                {
                nom : "Découverte",
                prix : "50€",
                entree : "",
                plat : "",
                dessert : ""},
             {
                nom : "Régional",
                prix : "40€",
                entree : "",
                plat : "",
                dessert : ""}
            ],
    };
  },
  mounted() {
    console.log("AVANT AFFICHAGE ! TEST");
    this.loadmenu();
    console.log("TESSSSST" + this.menu);

  },
  methods: {
    randomEntree(){
        this.entree = this.entrees[Math.floor(Math.random()*this.entrees.length)];
    },
    randomPlat(){
        this.plat = this.plats[Math.floor(Math.random()*this.plats.length)];
        console.log("test"+this.plat);
    },
    randomDessert(){
        this.dessert = this.desserts[Math.floor(Math.random()*this.desserts.length)];
    },
    randomMenu(){
        this.menu.push(this.menus[Math.floor(Math.random()*this.menus.length)]);
    },
    loadmenu(){
    for (let i =0;i <3; i++){
     this.randomMenu();
     this.randomEntree();
     this.randomPlat();
     this.randomDessert();
     this.menu[i].entree = this.entree;
     this.menu[i].plat = this.plat;
     this.menu[i].dessert= this.dessert;
    }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
