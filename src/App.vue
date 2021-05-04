<template>
  <div id="app">
    <div class="container">
      <div class="body">
        <TitleItems
          class="title-grouping"
          @selected-title="updateSelectedTitle"
        />

        <SidebarItem :selectedTitle="selectedTitle" />
      </div>
    </div>
  </div>
</template>

<script>
import SidebarItem from "./components/SidebarItem.vue";
import TitleItems from "./components/TitleItems.vue";
import titles from "./json/titles.json";

export default {
  components: {
    TitleItems,
    SidebarItem,
  },
  data() {
    return {
      showMetadata: false,
      selectedTitle: [],
      titles,
    };
  },
  methods: {
    updateSelectedTitle(titleInfo) {
      if (this.selectedTitle.length) {
        this.selectedTitle.pop();
        this.selectedTitle.push(titleInfo);
      } else {
        this.selectedTitle.push(titleInfo);
      }
      console.log("selectedTitle is now ", this.selectedTitle);
    },
  },
  computed: {},
};
</script>

<style>
body {
  background: #000000;
  box-sizing: content-box;
}
#app {
  overflow: hidden;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #ffffff;
}

.container {
  height: 100vh;
  width: 100vw;
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 1fr;
}

.body {
  display: grid;
  grid-template-columns: 3.5fr 1fr;
  overflow: hidden;
}

.title-grouping {
  overflow-y: scroll;
  padding: 20px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 3em;
  gap: 3em;
}

.sidebar {
  height: 100%;
  /* min-width: 240px;
  max-width: 260px; */
  position: fixed;
  z-index: 1;
  top: 0;
  right: 0;
  background-color: #000;
  overflow-x: hidden;
}
</style>
