<template>
  <v-dialog
    v-model="dialog"
    scrollable
    fullscreen
    persistent
    :overlay="false"
    width="700"
    transition="dialog-transition"
    @click="dialog = !dialog"
  >
    <Alert />
  </v-dialog>
  
  <v-container
    class="animate__animated animate__fadeIn animate__shakeY mx-auto"
  >
    <div class="mt-16 pa-16"></div>
    <div class="mt-10 pa-10"></div>

    <h1 class="title text-center text-white">Hello Witch, Wizard</h1>
    <h2 class="sub-title text-center text-white">
      Welcome to the Department of Computer Science
    </h2>

    <div class="text-center">
      <v-btn
        class="ma-10 border-opacity-0 bg-white"
        rounded
        size="large"
        color="white"
        to=""
        @click="dialog = !dialog"
        >Start</v-btn
      >
    </div>
  </v-container>
</template>

<script setup>
// import { onMounted, ref } from "vue";
const dialog = ref(false);
// const audio = ref(null);
// const hasPlayed = ref(false);

// onMounted(() => {
//   // hasPlayed.value = sessionStorage.getItem("hasPlayedAudio") === "true";

//   // if (!hasPlayed.value) {
//   //   const audioElement = new Audio("music/hedwig.mp3"); // Ensure this is in the public/ folder
//   //   audioElement
//   //     .play()
//   //     .then(() => {
//   //       hasPlayed.value = true;
//   //       sessionStorage.setItem("hasPlayedAudio", "true");
//   //     })
//   //     .catch((err) => {
//   //       console.warn("Autoplay ถูกบล็อกโดยเบราว์เซอร์:", err);
//   //     });

//   //   // Optional: store the instance if needed later
//   //   audio.value = audioElement;
//   // }
// });
</script>

