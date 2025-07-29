<!-- <script setup lang="ts">
const props = defineProps<{
  quizIndex: number
  pages: string
}>()
</script> -->


<template>
  <v-container class="pa-md-12 text-center ">
    <div class="mt-16 pa-16"></div>

    <v-alert
      class="mx-auto mb-4 border-white"
      icon="$warning"
      color="amber"
      max-width="700"
      rounded="lg"
      title="Warning the testing version"
    />
   <div class="text-center text-white pa-2" >
     <p class="ma-2">You can press <v-icon>mdi-menu</v-icon>  for change Page or Click Here </p>
     <p class="ma-2"><v-btn to="quiz">Quiz game</v-btn> <v-btn to="moss">Moss game</v-btn> <v-btn to="vial">Vial game</v-btn></p>
   </div>
  </v-container>
</template>