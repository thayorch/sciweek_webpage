<template>
  <v-container class="animate__animated animate__fadeIn animate__shakeY">
    <h1 class="text-center text-white">Quiz {{ quiz_count }}</h1>
    <div class="ma-8 gamepanel mx-auto text-center">
      
      <h1 class="text-center text-white">Guess the shadow</h1>
      <div class="picture">
        <img src="~/assets/quiz1/conan.jpg" height="200" alt="">
      </div>
      <div class="answer" >
        <v-row no-gutters>
          <v-col class="pa-2 ma-2">
            <v-card
              class="mx-auto"
              width="200"
              height="55"
              subtitle=""
              title="Answer 1"
              link
            ></v-card>
          </v-col>

          <v-col class="pa-2 ma-2">
            <v-card
              class="mx-auto"
              width="200"
              height="55"
              title="Answer 2"
              link
            ></v-card>
          </v-col>

          <v-col class="pa-2 ma-2">
            <v-card
              class="mx-auto"
              width="200"
              height="55"
              title="Answer 3"
              link
            ></v-card>
          </v-col>

          <v-col class="pa-2 ma-2">
            <v-card
              class="mx-auto"
              width="200"
              height="55"
              title="Answer 4"
              link
            ></v-card>
          </v-col>
        </v-row>
      </div>
      <!-- <v-btn
        v-if="!alert_status"
        class="ma-10 border-opacity-0"
        rounded
        color="white"
        @click="updateCount"
      >
        {{ btn_option }}
      </v-btn> -->
    </div>
  </v-container>
</template>

<script setup lang="ts">
const alert_status = ref(false);
const quiz_count = ref<number>(1);
const btn_option = ref<string>("Next");

const updateCount = () => {
  quiz_count.value++;
  if (quiz_count.value === 10) {
    alert_status.value = !alert_status.value;
  }
};
</script>

<style lang="scss">
.gamepanel {
  width: 50vw;
  height: 70vh;
  background: #ffffff77;
}

</style>
