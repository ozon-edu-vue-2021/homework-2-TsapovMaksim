<template>
  <div class="directory">
    <div>
      <component :is="iconsForType[spisObject.type]" />
      {{ spisObject.name }}
      <button
        v-if="spisObject.type === 'directory'"
        @click="toggleOpenDirectory"
      >
        {{ isDirectoryOpen ? 'Close' : 'Open' }}
      </button>
    </div>

    <template v-if="isDirectoryOpen">
      <div
        v-for="(item, index) in spisObject.contents"
        :key="String(item.name + index)"
      >
        <tree-dir
          v-if="item.type === 'directory'"
          :spisObject="item"
          :currentIndex="`${index}${currentIndex}`"
        />
        <div
          v-else
          @click="onItemClick(index)"
          :class="{
            selected: activeItem.value === `${index}${currentIndex}`,
          }"
        >
          <component :is="iconsForType[item.type]" />
          {{ item.name }}
        </div>
      </div>
    </template>
  </div>
</template>

<script>
import FolderIcon from './icons/Folder.vue';
import FileIcon from './icons/File.vue';
import LinkIcon from './icons/Link.vue';

export default {
  name: 'TreeDir',
  components: {
    FolderIcon,
    FileIcon,
    LinkIcon,
  },
  inject: ['selectedItem', 'setSelectedItem'],
  props: {
    spisObject: {
      type: Object,
      required: true,
    },
    currentIndex: {
      type: String,
      default: '',
    },
  },
  data: function() {
    return {
      iconsForType: {
        file: FileIcon,
        directory: FolderIcon,
        link: LinkIcon,
      },
      isDirectoryOpen: false,
      activeItem: this.selectedItem,
    };
  },
  methods: {
    toggleOpenDirectory() {
      this.isDirectoryOpen = !this.isDirectoryOpen;
    },
    onItemClick(index) {
      const newCurrentIndex = `${index}${this.currentIndex}`;
      this.setSelectedItem(newCurrentIndex);
    },
  },
};
</script>

<style>
.directory {
  padding-left: 10px;
  border-left: 1px solid black;
  margin-bottom: 10px;
}

.selected {
  background-color: rgba(180, 143, 143, 0.5);
}
</style>
