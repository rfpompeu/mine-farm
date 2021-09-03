<template>
  <v-container>
    <v-row class="text-h4 my-5">Frutas</v-row>
    <v-row>
      <card
        name="Maçã"
        city="Belém"
        state="Pa"
        type="Fuji"
        img="apple"
        obs="Primeira experiência com a espécie de maçã"
        plant
      />
      <card
        name="Café"
        city="Manaus"
        state="AM"
        img="coffe"
        type="Desconhecida"
        obs="A última safra não foi lucrativa"
        plant
      />
    </v-row>
    <v-row class="text-h4 my-5">Animais</v-row>
    <v-row>
      <card
        name="Porcos"
        city="Manaus"
        state="AM"
        type="Piétrain"
        img="pig"
        obs="Primeira criação de porcos"
      />
      <card
        name="Galinhas"
        img="chicken"
        type="ISA Brown"
        city="Belém"
        state="PA"
        obs="Criação para consumo familiar"
      />
    </v-row>
    <v-row class="text-h4 my-5">Legumes</v-row>
    <v-row>
      <card
        name="Cenoura"
        city="Belém"
        state="PA"
        type="Tendersweet"
        img="carrot"
        obs="Primeira plantação de cenoura"
        plant
      />
      <card
        name="Beterraba"
        city="Belém"
        state="PA"
        type="Beta vulgaris"
        img="beetroot"
        obs="Primeira experiência com a espécie"
        plant
      />
    </v-row>
  </v-container>
</template>

<script>
import Card from "../components/Home/Card";
export default {
  name: "Home",

  components: {
    Card,
  },
};
</script>
