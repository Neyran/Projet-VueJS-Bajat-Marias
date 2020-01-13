<template>
    <div>
                
        <H3>Nos menus</H3>
            <li>Menu 1</li>
                <ol>
                    <li>Entrée</li>
                    <p>Infos necessaire</p>
                    <li>Plat</li>
                    <p>Infos necessaire</p>
                    <li>Dessert</li>
                    <p>Infos necessaire</p>
                </ol>
            <li>Menu 2</li>
            <ol>
                <li>Entrée</li>
                <p>Infos necessaire</p>
                <li>Plat</li>
                <p>Infos necessaire</p>
                <li>Dessert</li>
                <p>Infos necessaire</p>
            </ol>
            <li>Menu 3</li>
            <ol>
                <li>Entrée</li>
                <p>Infos necessaire</p>
                <li>Plat</li>
                <p>Infos necessaire</p>
                <li>Dessert</li>
                <p>Infos necessaire</p>
            </ol>
        <h3>A la carte</h3>
        <ul>
        <li v-bind="randomEntree">
            document.write(randomEntree())
            <p v-bind:src="randomEntree"></p>
        </li>
    </ul>

        <p>Tu me fais un V-for i=30 avec 10 entrées 10 plats et 10 dessert aléatoire parmis ta liste</p>

    </div>
</template>

<script>
export default {
  name: "RestaurantMenu",
  props: {},
  data: function() {
    return {
        entrees: ['Salade de chèvre chaud','Soupe aux légumes verts','Soupe aux champignons',"Tartare de saumon et d'avocat",'Tartine de saumon fumé au fromage frais','Avocat aux crevettes','Mini quiches aux asperges et tomates','Salade de betterave','Chaussons aux légumes','Bricks à la viande','Velouté de petits pois','Galettes de crabe','Flan de courgettes','aboulé libanais',"Champignons à l'ail",'Bâtonnets de mozzarella frits','Oeufs mimosa au thon','Beignets de crevettes','Salade de carottes acidulée','Velouté de courgettes','Tartelettes courgettes chèvre','Gaspacho',"Smoothie à l'avocat",'Oeufs mimosa au thon','Feuilletés saumon épinards','Macédoine de légumes','Feuilletés à la coppa','Velouté de lentilles','Soupe de potiro','Soupe au fenouil','Oeufs brouillés au jambon','Soufflé aux courgettes','Chaussons aux légumes'],
        plat : ["Filet mignon en croûte","Lasagnes à la bolognaise","Sauté de veau au chorizo","Hachis Parmentier","Boeuf Bourguignon rapide","Amour de saumon en papillote","Poulet à la moutarde, à l'estragon et aux champignons","Filet mignon de porc au Maroilles","Chili con carne","Endive jambon","Couscous poulet et merguez","Gratin Dauphinois","Quiche lorraine","Tarte tatin de légumes","Lapin à la moutarde maison","Poulet basquaise","Carbonades flamandes traditionnelles","Boeuf braisé aux carottes","Crevettes au curry","Rôti de porc de Dijon","Ratatouille","Parmentier de confit de canard","Tajine d'agneau aux pruneaux","Pâte à pizza fine","Tartiflette","Riz au curry et crevettes","Spaghetti alla carbonara","Pâtes au saumon fumé","Bruschetta tomates mozzarella","Poulet au curry coco","Crevettes à l'indienne","Quiche aux poireaux"],
        dessert : ["Tarte chocolat poire","Tarte au citron meringuée","Verrines de framboises","Tarte aux pommes","Cake aux pépites de chocolat","Crème au chocolat","Gâteau moelleux aux pêches","Tarte tatin aux pommes","Tarte tatin aux pommes","Crumble aux pommes","Madeleines","Quatre-quarts maison","Tiramisu au café","Clafoutis aux pommes","Cake aux bananes et pépites de chocolat","Brownies","Tiramisu aux fraises","Cookies","Pancakes"],
        menus : [ {
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
            nom : "provencal",
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
    console.log("AVANT AFFICHAGE !");
  },
  methods: {
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
