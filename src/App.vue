<template>
  <div id="app">
    <folder-tree :spisObject="getData()" />
  </div>
</template>

<script>
import FolderTree from './components/FolderTree.vue';
import data from '../public/static/node_modules.json';
// const mockData = {
//   type: 'directory',
//   name: 'asdf',
//   contents: [
//     {
//       type: 'file',
//       name: 'LICENSE',
//     },
//     {
//       type: 'file',
//       name: 'README.md',
//     },
//     {
//       type: 'directory',
//       name: 'lib',
//       contents: [
//         {
//           type: 'file',
//           name: 'index.js',
//         },
//         {
//           type: 'directory',
//           name: 'lib',
//           contents: [
//             {
//               type: 'file',
//               name: 'index.js',
//             },
//             {
//               type: 'directory',
//               name: 'lib',
//               contents: [
//                 {
//                   type: 'file',
//                   name: 'index.js',
//                 },
//                 {
//                   type: 'directory',
//                   name: 'lib',
//                   contents: [
//                     {
//                       type: 'file',
//                       name: 'indexd.js',
//                     },
//                     {
//                       type: 'file',
//                       name: 'indexd.fjs',
//                     },
//                     {
//                       type: 'file',
//                       name: 'indexds.js',
//                     },
//                     {
//                       type: 'file',
//                       name: 'indexd.js',
//                     },
//                   ],
//                 },
//               ],
//             },
//           ],
//         },
//       ],
//     },
//     {
//       type: 'file',
//       name: 'package.json',
//     },
//   ],
// };

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
