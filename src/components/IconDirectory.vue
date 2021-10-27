<template>
  <component :is="iconsForType[iconType]" />
</template>

<script>
import FolderIcon from './icons/Folder.vue';
import FileIcon from './icons/File.vue';
import LinkIcon from './icons/Folder.vue';

export default {
  name: 'IconDirectory',
  components: {
    FolderIcon,
    FileIcon,
    LinkIcon,
  },
  props: {
    iconType: {
      type: String,
      required: true,
    },
  },
  data: function() {
    return {
      iconsForType: {
        file: FileIcon,
        directory: FolderIcon,
        link: LinkIcon,
      },
    };
  },
};
</script>
