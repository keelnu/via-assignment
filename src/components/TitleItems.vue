<template>
  <div class="title-gallery">
    <div class="gallery-item" v-for="(title, index) in titles" :key="title.id">
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
        width="320"
        height="515"
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
      console.log(
        `You selected ${name}, id: ${id}. It's rated ${rating}. Description: ${description}`
      );
    },
  },
};
</script>

<style scoped>
.title-gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(18rem, 1fr));
  grid-gap: 0.75rem;
  padding: 0 3rem;
}

.gallery-item img {
  margin-top: 2rem;
}

.active:hover {
  opacity: 0.4;
  transition: 0.5s ease;
  backface-visibility: hidden;
}

h2 {
  margin: 0;
  padding: 0;
  font-size: 20px;
}
</style>