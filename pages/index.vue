<template lang="html">
  <div >
    <v-app id="gg">
    <div>
      <v-text-field v-model="query" label="ใส่ชื่อAnime" outlined dense></v-text-field>
      <v-row justify="center">
      <v-btn @click="handleSearchAnime">Search</v-btn>
      </v-row>
    </div>
    <v-divider class="mt-2 mb-2"></v-divider>
    <div class="d-flex flex-wrap">
      <v-card
        v-for="anime in results"
        :key="anime.mal_id"
        class="ma-2"
        max-width="3500"
        outlined
        @click="handleAnimeClick(anime)"
      >
        <v-list-item three-line>
          <img
            :src="anime.image_url"
            alt=""
            :style="{ width: '80px', marginTop: '10px' }"
          />
          <v-list-item-content>
            <div class="overline mb-4">Airing :  {{ anime.airing }}</div>
            <v-list-item-title class="headline mb-1">
              {{ anime.title }}</v-list-item-title
            >
            <v-list-item-subtitle>
              {{ anime.synopsis }}
            </v-list-item-subtitle>
          </v-list-item-content>

          
        </v-list-item>
      </v-card>
    </div>
    </v-app>
  </div>
  
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      query: "",
      results: [],
    };
  },
  methods: {
    handleSearchAnime() {
      const url = `https://api.jikan.moe/v3/search/anime?q=${this.query}&page=1'+this.query+' `;
      axios.get(url).then((res) => {
        console.log(res.data);
        this.results = res.data.results;
      });
    },
    handleAnimeClick(anime) {
      console.log("ANIME", anime);
      window.location = anime.url;
    },
  },
};
</script>

<style lang="css" scoped>
#gg {
  background-image: url("https://wallpaperaccess.com/full/6313.jpg");
  background-size: cover;
}
</style>
