<script setup>
import { ref } from "vue";
import SearchComponent from "./SearchComponent.vue";

const emit = defineEmits(["miEvento"]);

let showVideo = ref(false);
let showVideoSmall = ref(false);
let showVideoPrincipal = ref(false);
let resultSearch = ref("2UCBbcBT5Es");

function visionFrame(e) {
  showVideo.value = e;
  showVideoSmall.value = false;
  showVideoPrincipal.value = false;
}
function visionFrameSmall(e) {
  showVideoSmall.value = e;
  showVideo.value = false;
  showVideoPrincipal.value = false;
}

function visionFramePrincipal(e) {
  showVideoPrincipal.value = e;
  showVideo.value = false;
  showVideoSmall.value = false;
}

function recibirDato(e) {
  resultSearch.value = e;
  showVideoPrincipal.value = true;
  showVideo.value = false;
  showVideoSmall.value = false;
}
</script>

<template>
  <SearchComponent @miEvento="recibirDato"></SearchComponent>
  <div v-if="showVideo" class="videoYoutube" style="margin-top: 20px">
    <button @click="visionFrame(false)" type="button" class="btn btn-danger">
      Close
    </button>
    <iframe
      width="100%"
      height="415"
      src="https://www.youtube.com/embed/m_GoB8SFOeM?autoplay=1"
      title="YouTube video player"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
      referrerpolicy="strict-origin-when-cross-origin"
      allowfullscreen
    ></iframe>
  </div>

  <div class="main-container">
    <div v-if="!showVideoPrincipal" class="left margin-20 flip-card">
      <div class="flip-card-inner neon-border">
        <div class="flip-card-front">
          <img
            src="https://cdn.digitaldjtips.com/app/uploads/2012/11/09145904/i-love-house-music.jpg"
            alt="Avatar"
            style="width: 100%; height: 100%"
          />
        </div>
        <div
          @click="visionFramePrincipal(true)"
          class="flip-card-back neon-border"
        >
          <img
            src="https://i.ytimg.com/vi/2UCBbcBT5Es/hq720.jpg?sqp=-oaymwEnCNAFEJQDSFryq4qpAxkIARUAAIhCGAHYAQHiAQoIGBACGAY4AUAB&rs=AOn4CLDhoVxfjzkpTpkF2cFTRSJxf6MRlg"
            alt="Avatar"
            style="width: 100%; height: 100%"
          />
          <i class="fa-solid fa-play z-index-up"></i>
        </div>
      </div>
    </div>
    <div v-else class="neon-border margin-20 left">
      <iframe
        width="100%"
        height="100%"
        :src="'https://www.youtube.com/embed/' + resultSearch + '?autoplay=1'"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
        referrerpolicy="strict-origin-when-cross-origin"
        allowfullscreen
      ></iframe>
    </div>

    <div class="right">
      <div class="right-top">
        <div
          @click="visionFrame(true)"
          class="right-top-1 margin-20 neon-border"
        >
          <img
            src="https://borsarionline.b-cdn.net/media/catalog/product/cache/1/image/650x/040ec09b1e35df139433887a97daa66f/d/j/dj-202_main.jpg"
            class="thumbnail width-100"
          />
          <i class="fa-solid fa-play z-index-up"></i>
        </div>
        <div class="arrow">
          <span></span>
          <span></span>
          <span></span>
        </div>
        <div class="right-top-2 margin-20">
          <div class="testo neon-border">
            <h3>Sunset Deep House Mix</h3>
            <p>
              Afro House, deep, melodic, tech, funky, organic, groovy house mix
              by Maldo para dejar de fondo incluyendo temas de Adam Port,
              Keinemusic, Black Coffee, Diplo, HUGEL, Alex Wann, Moojo, Rihanna,
              RAFFA GUIDO, Rampa, Drake, &ME, Cercle y Adriatique.
            </p>
          </div>
        </div>
      </div>

      <div class="right-bottom">
        <div class="right-bottom-1 neon-border margin-20"></div>
        <div
          @click="visionFrameSmall(true)"
          class="right-bottom-2 neon-border margin-20"
        >
          <div
            v-if="!showVideoSmall"
            class="d-flex justify-content-center width-100"
          >
            <img
              src="https://borsarionline.b-cdn.net/media/catalog/product/cache/1/image/650x/040ec09b1e35df139433887a97daa66f/d/j/dj-202_main.jpg"
              class="thumbnail width-100"
            />
            <i class="fa-solid fa-play z-index-up"></i>
          </div>
          <iframe
            v-else
            width="100%"
            height="100%"
            src="https://www.youtube.com/embed/LxsT5bYUhbM?autoplay=1"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            referrerpolicy="strict-origin-when-cross-origin"
            allowfullscreen
          ></iframe>
        </div>
      </div>
    </div>
  </div>
</template>
