<template>
  <v-card class="mx-auto" max-width="400">
    <v-img
      class="white--text align-end"
      height="200px"
      :src="get_image_by_name(img)"
    >
      <v-card-title>{{ name }}</v-card-title>
    </v-img>

    <v-card-subtitle class="pb-0"> {{ city }} - {{ state }}</v-card-subtitle>

    <v-card-text class="text--primary">
      <div v-if="plant">Espécie: {{ type }}</div>
      <div v-else>Raça: {{ type }}</div>

      <div>Observação: {{obs}}</div>
    </v-card-text>

    <v-card-actions>
      <v-btn color="orange" text> VIsualizar </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: "Card",
  props: {
    name: String,
    city: String,
    state: String,
    obs: String,
    plant: Boolean,
    type: String,
    img: String
  },
  methods: {
    get_image_by_name(name) {
      const images = {
        apple: "https://images.pexels.com/photos/5529540/pexels-photo-5529540.jpeg?cs=srgb&dl=pexels-zen-chung-5529540.jpg&fm=jpg",
        pig: "https://images.pexels.com/photos/45869/pig-domestic-pig-suckle-piglet-45869.jpeg?cs=srgb&dl=pexels-pixabay-45869.jpg",
        chicken: "https://images.pexels.com/photos/2134180/pexels-photo-2134180.jpeg?cs=srgb&dl=pexels-quang-nguyen-vinh-2134180.jpg",
        coffe: "https://images.pexels.com/photos/7125465/pexels-photo-7125465.jpeg?cs=srgb&dl=pexels-michael-burrows-7125465.jpg&fm=jpg",
        carrot: "https://images.pexels.com/photos/143133/pexels-photo-143133.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260",
        beetroot: "https://images.pexels.com/photos/5502850/pexels-photo-5502850.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260"
      };
      return images[name];
    },
  },
};
</script>
