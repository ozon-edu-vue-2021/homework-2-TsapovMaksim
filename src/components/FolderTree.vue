<template>
  <div class="">
    <tree-dir :spisObject="spisObject" />
  </div>
</template>

<script>
import TreeDir from './TreeDir.vue';
export default {
  name: 'FolderTree',
  components: {
    TreeDir,
  },
  provide() {
    return {
      selectedItem: { value: '' },
      setSelectedItem(str) {
        this.selectedItem.value = str;
      },
    };
  },
  props: {
    spisObject: {
      type: Object,
      required: true,
    },
  },
};
</script>
