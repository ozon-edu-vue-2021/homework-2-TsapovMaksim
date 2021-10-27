<template>
  <div class="directory">
    <div class="directory__folder" @click="toggleOpenDirectory">
      <icon-directory :iconType="spisObject.type" />
      <span class="directory__folder-text">{{ spisObject.name }}</span>
      <div
        class="arrow"
        :class="{ arrow_bottom: isDirectoryOpen }"
        v-if="spisObject.type === 'directory'"
      ></div>
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
          class="directory__file"
          :class="{
            selected: activeItem.value === `${index}${currentIndex}`,
          }"
        >
          <icon-directory :iconType="item.type" />
          {{ item.name }}
        </div>
      </div>
    </template>
  </div>
</template>

<script>
import IconDirectory from './IconDirectory.vue';

export default {
  name: 'TreeDir',
  components: {
    IconDirectory,
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
      isDirectoryOpen: false,
      activeItem: this.selectedItem,
    };
  },
  methods: {
    toggleOpenDirectory() {
      const difference =
        this.selectedItem.value.length - this.currentIndex.length;
      const slicedByDifference = this.selectedItem.value.slice(difference);

      if (slicedByDifference === this.currentIndex) {
        this.setSelectedItem('');
      }

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

.directory__folder {
  cursor: pointer;
  display: inline-flex;
}

.directory__folder-text {
  margin-left: 2px;
}

.directory__file {
  cursor: pointer;
}

.arrow {
  width: 8px;
  height: 8px;
  border-top: 4px solid #6e18c0;
  border-right: 4px solid #6e18c0;
  transform: translateX(3px) rotate(135deg);
  margin-left: 5px;
}

.arrow_bottom {
  transform: rotate(-45deg) translateY(6px) translateX(-2px);
}

.selected {
  background-color: rgba(180, 143, 143, 0.5);
}
</style>
