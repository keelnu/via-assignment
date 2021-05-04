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
  width: 80%;
  padding-left: 1.5rem;
  margin: 0;
  overflow: hidden;
}

h2 {
  font-size: 24px;
  margin-bottom: 0.5rem;
  padding: 0;
}

p {
  font-size: 16px;
  margin: 0;
  padding: 0;
}
</style>