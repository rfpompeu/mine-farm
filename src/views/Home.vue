<template>
  <v-container>
    <v-row class="text-h4 my-5">Frutas</v-row>
    <v-row>
      <card name='Maçã' city='Belém' state='Pa' type='Fuji' img='apple' obs='Primeira experiência com a espécie de maçã' plant/>
      <card name='Café' img='coffe'/>
    </v-row>
    <v-row class="text-h4 my-5">Animais</v-row>
    <v-row>
      <card name='Porcos' city='Manaus' state='AM' type='Piétrain' img='pig' obs='Primeira çriação de porcos'/>
      <card name='Galinhas' img='chicken' />
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
