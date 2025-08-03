<script setup>
import { ref, defineEmits } from 'vue';


const emit = defineEmits(['miEvento'])

const searchTesto = ref("");

function startSearch() {
  const url = searchTesto.value;

  // Extraer el ID del video
  let videoId = null;

  try {
    const parsedUrl = new URL(url);
    videoId = parsedUrl.searchParams.get("v");

    // Si es un enlace corto como https://youtu.be/VIDEO_ID
    if (!videoId && parsedUrl.hostname === "youtu.be") {
      videoId = parsedUrl.pathname.slice(1);
    }
    emit('miEvento', videoId) // Emitimos el evento y enviamos el dato
    console.log("Video ID:", videoId);
  } catch (error) {
    console.error("Invalid URL:", error);
  }
}
</script>

<template>

<div class="mb-3 search" style="width: 100%;">
    <div class="search">
        <input v-model="searchTesto" placeholder="Paste the youtube video url for start the search"  type="text" class="form-control" aria-label="Small" aria-describedby="inputGroup-sizing-sm">
        <button  @click="startSearch" type="button" class="btn btn-info">
          <i class="fa-solid fa-headphones"></i>
        </button>
    </div>
</div>


</template>

<style>
.search{
    width: 80%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.search button{
  margin-left: 10px;
  background-color: rgb(0, 234, 234);
}
</style>