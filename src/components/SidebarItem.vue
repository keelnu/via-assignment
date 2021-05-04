<template>
  <div class="title-metadata" v-for="item in selectedTitle" :key="item.id">
    <h2>{{ item.name }}</h2>
    <p>Rating: {{ item.rating }}</p>
    <p>{{ item.description }}</p>
  </div>
</template>

<script>
export default {
  name: "SidebarItem",
  props: {
    selectedTitle: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.title-metadata {
  padding: 0 3rem 0 2rem;
  /* padding-left: 1rem; */
}

h2 {
  font-size: 24px;
  margin-bottom: 0.25rem;
  padding: 0;
}

p {
  font-size: 16px;
  margin: 0;
  padding: 0;
}
</style>