<template>
  <v-app>
    <v-main class="main-bg">
      <Navbar/>

      <slot />
    </v-main>
  </v-app>
</template>

<style lang="scss">
.main-bg {
  background: url("~/assets/background.jpg");
  background-size: cover;
  background-position: center;
}
</style>
