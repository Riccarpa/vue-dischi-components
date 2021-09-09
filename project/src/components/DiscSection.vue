<template>
  <main class="container">
    <select v-model="selected">
      <option>All</option>
      <option v-for="(genre, index) in genreCatch" :key="index">{{
        genre
      }}</option>
    </select>
    <section id="album-container">
      <Loader v-if="!albumList" />
      <Card
        v-else
        v-for="(album, index) in albumListSorted"
        :key="index"
        :album="album"
        v-show="genreFilter(album)"
      />
    </section>
  </main>
</template>

<script>
import axios from "axios";
import Card from "@/components/Card.vue";
import Loader from "@/components/Loader.vue";

export default {
  name: "DiscSection",
  components: {
    Card,
    Loader,
  },

  data() {
    return {
      albumList: [],
      selected: "All",
    };
  },
  computed: {
    albumListSorted() {
      const albumSorted = this.albumList.slice(0).sort(function(a, b) {
        return a.year - b.year;
      });
      return albumSorted;
    },
    genreCatch() {
      const genres = [];
      this.albumList.forEach((element) => {
        if (!genres.includes(element.genre)) {
          genres.push(element.genre);
        }
      });

      return genres;
    },
  },
  methods: {
    genreFilter(album) {
      if (this.selected === album.genre || this.selected === "All") {
        return true;
      }
    },
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        const response = res.data.response;
        response.forEach((element) => {
          this.albumList.push(element);
        });
      });
  },
};
</script>

<style></style>
