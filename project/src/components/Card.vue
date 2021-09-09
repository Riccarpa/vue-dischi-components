<template>
  <div class="card">
    <img :src="album.poster" alt="New Jersey" />
    <h2 class="title">{{ album.title }}</h2>
    <address class="author">{{ album.author }}</address>
    <time datetime="1988" class="year">{{ album.year }}</time>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["album"],
};
</script>

<style></style>
