<template>
  <div id="app">
    <folder-tree :spisObject="getData()" />
  </div>
</template>

<script>
import FolderTree from './components/FolderTree.vue';
import data from '../public/static/node_modules.json';

export default {
  name: 'App',
  components: {
    FolderTree,
  },
  data: function() {
    return {};
  },

  methods: {
    getData() {
      return data;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
