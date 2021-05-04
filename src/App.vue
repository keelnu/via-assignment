<template>
  <div id="app">
    <div class="container">
      <div class="body">
        <TitleItems
          class="title-grouping"
          @selected-title="updateSelectedTitle"
        />
        <aside class="sidebar">
          <SidebarItem :selectedTitle="selectedTitle" />
        </aside>
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
      // console.log("selectedTitle is now ", this.selectedTitle);
    },
  },
};
</script>

<style>
body {
  background: #000000;
  box-sizing: content-box;
  overflow-y: hidden;
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
  height: 100vh;
  grid-template-columns: 3fr 1fr;
  overflow: hidden;
}

.sidebar {
  position: sticky;
  z-index: 1;
  top: 0;
  right: 0;
  background-color: #000;
  overflow: hidden;
}
</style>
