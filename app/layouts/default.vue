<template>
  <v-app>
    <v-main class="main-bg">
      <div class="bg-transparent d-flex justify-end px-4">
  <!-- Button container aligned to the right -->
  <div class="d-flex gap-2">
    <v-btn
      variant="plain"
      class="text-white"
      size="large"
      density="compact"
      icon="mdi-arrow-left-bottom"
      to="/"
    />
    <FullscreenBtn />
  </div>
</div>

      
      <slot />
    </v-main>
  </v-app>
</template>


<style lang="scss">
.main-bg {
  background: url("~/assets/background.jpg");
  background-size: cover;
}
</style>
