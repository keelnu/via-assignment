<template>
  <div class="title-gallery">
    <div class="gallery-item" v-for="title in titles" :key="title.id">
      <img
        :src="title.images[0].url"
        :class="{ active: isActive }"
        @click="
          selected(
            title.id,
            title.name,
            title.titleRating,
            title.description.short
          )
        "
        width="260"
        height="390"
      />
      <h2>{{ title.name }}</h2>
    </div>
  </div>
</template>

<script>
import titles from "../json/titles.json";

export default {
  name: "TitleItems",
  emits: {
    "selected-title"(payload) {
      if (
        typeof payload.id === "number" &&
        typeof payload.name === "string" &&
        typeof payload.rating === "string" &&
        typeof payload.description === "string"
      ) {
        return true;
      } else {
        return false;
      }
    },
  },
  data() {
    return {
      isActive: true,
      titles,
    };
  },
  methods: {
    selected(id, name, rating, description) {
      this.$emit("selected-title", {
        id: id,
        name: name,
        rating: rating,
        description: description,
      });
      // console.log(
      //   `You selected ${name}, id: ${id}. It's rated ${rating}. Description: ${description}`
      // );
    },
  },
};
</script>

<style scoped>
.title-gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(16rem, 1fr));
  gap: 1.5rem 1.25rem;
  padding: 1.5rem;
  overflow-y: scroll;
}

.active:hover {
  opacity: 0.4;
  transition: 0.5s ease;
  backface-visibility: hidden;
}

.gallery-item h2 {
  width: 70%;
  margin: 0;
  padding: 0 20px 0 0;
  font-size: 18px;
}
</style>