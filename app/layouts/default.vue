<template>
  <v-app>
    <v-main class="main-bg">
      <!-- <AppHeader/> -->
      <v-btn
        variant="plain"
        class="text-white text-center"
        size="large"
        density="compact"
        icon="mdi-arrow-left-bottom"
        to="/"
      ></v-btn>
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
