<template>
  <v-btn
    v-if="!fullscreen"
    variant="plain"
    class="text-white text-center"
    size="large"
    density="compact"
    icon="mdi-fullscreen"
    z
    @click="toggleFullscreen"
  ></v-btn>

  <v-btn
    v-if="fullscreen"
    variant="plain"
    class="text-white text-center"
    size="large"
    density="compact"
    icon="mdi-fullscreen"
    @click="toggleFullscreen"
  ></v-btn>
</template>

<script setup lang="ts">
const fullscreen = ref<boolean>(false);
const toggleFullscreen = () => {
  if (!document.fullscreenElement) {
    document.documentElement.requestFullscreen();
    fullscreen.value = true;
  } else {
    document.exitFullscreen();
    fullscreen.value = false;
  }
};
</script>
