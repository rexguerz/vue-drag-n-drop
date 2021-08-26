<template>
  <div class="home">
    <h1>Drag-n-Drop File</h1>
    <DropZone @drop.prevent="drop" @change="selectedFile"/>
    <span class="file-info">File: {{ dropzoneFile.name }}</span>
  </div>
</template>

<script>
import DropZone from '@/components/DropZone'
import { ref } from "vue"

export default {
  name: 'Home',
  components: {
    DropZone,
  },

  setup() {
    let dropzoneFile = ref("")

    const drop = (event) => {
      dropzoneFile.value = event.dataTransfer.files[0]
    }

    const selectedFile = () => {
      dropzoneFile.value = document.querySelector('.dropzoneFile').files[0]
    } 

    return { dropzoneFile, drop, selectedFile } 
  }
}
</script>

<style lang="scss" scoped>
.home {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #f1f1f1;

  h1 {
    font-size: 40px;
    margin-bottom: 32px;
  }

  .file-info {
    margin-top: 32px;
  }
}
</style>