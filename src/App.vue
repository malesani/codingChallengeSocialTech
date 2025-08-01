<script setup>
import { ref, onMounted  } from 'vue';
import Header from './components/Header.vue'
import VideoComponent from './components/VideoComponent.vue';
import Loader from './components/Loader.vue';

let isLoading = ref(true);

onMounted(() => {
  setTimeout(() => {
    isLoading.value = false;
  }, 4000);
});
</script>

<template>
  <Loader v-if="isLoading"></Loader>
  <Header></Header>
  <VideoComponent v-if="!isLoading"></VideoComponent>
</template>

