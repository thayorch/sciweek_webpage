<template>
  <v-container
    class="sub-title animate__animated animate__fadeIn animate__shakeY mx-auto"
  >
    <div class="mt-16 pa-16"></div>
    <h1 class="text-center text-white">! Thanks For Playing !</h1>
    <h2 class="text-center text-white">You got the Goblet of Fire</h2>

    <div class="text-center">
      <v-img
        :src="img_source"
        height="200"
        width="200"
        class="text-center mx-auto"
      ></v-img>
    </div>

    <p class="text-center text-white">You can go to the entrance</p>
    <div class="text-center">
      <v-btn class="ma-10 border-opacity-0" rounded color="white" to="/"
        >Dashbord</v-btn
      >
    </div>
  </v-container>
</template>

<script setup>
const img_source = "vials/goblet.png";
</script>
