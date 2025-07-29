<template>
  <audio ref="audioRef" :src="audioSources[quizIndex]" preload="auto"></audio>
  <v-dialog
    v-model="alertCorrect"
    scrollable
    persistent
    :overlay="false"
    max-width="500px"
    transition="dialog-transition"
    class="animate__animated animate__fadeIn animate__shakeY mx-auto"
  >
    <Correct :quizIndex="quizIndex" pages="moss" />
  </v-dialog>

  <v-dialog
    v-model="alertIncorrect"
    scrollable
    persistent
    :overlay="false"
    max-width="500px"
    transition="dialog-transition"
    class="animate__animated animate__fadeIn animate__shakeY mx-auto"
  >
    <Incorrect :quizIndex="quizIndex" pages="moss" />
  </v-dialog>

  <v-container class="animate__animated animate__fadeIn animate__shakeY">
    <h1 class="text-center text-white">Quiz {{ quizIndex + 1 }} / 5</h1>

    <div class="mt-8 gamepanel mx-auto text-center">
      <h1 class="text-center text-white">Guess the moss code</h1>

      <v-btn
        @click="playSound"
        icon="mdi-volume-high"
        height="120"
        width="120"
        class="mt-5 playsound"
      >
        <v-icon class="ma-2" color="white" size="35" style="cursor: pointer">
          mdi-volume-high
        </v-icon>
      </v-btn>

      <div class="option ma-8">
        <v-row>
          <v-col
            v-for="(data, index) in optionData[quizIndex]"
            :key="index"
            cols="6"
            class="pa-2"
          >
            <v-card
              class="mx-auto"
              size="large"
              :title="data.title"
              @click="checkAnswer(data.title)"
            ></v-card>
          </v-col>
        </v-row>
      </div>
    </div>
  </v-container>
</template>

<script setup lang="ts">
const router = useRouter();
const optionData = ref([
  [
    { title: ". _ _ . ." },
    { title: "_ _ . . ." },
    { title: "_ . _ . _" },
    { title: "_ . _ . ." },
  ],
  [
    { title: ". _ _ . ." },
    { title: "_ _ . . ." },
    { title: "_ . _ . _" },
    { title: "_ . _ . ." },
  ],
  [
    { title: ". _ _ . ." },
    { title: "_ _ . . ." },
    { title: "_ . _ . _" },
    { title: "_ . _ . ." },
  ],
  [
    { title: ". _ _ . ." },
    { title: "_________" },
    { title: ". . . . ." },
    { title: "_ . _ . ." },
  ],
  [
    { title: ". _ _ . ." },
    { title: "_________" },
    { title: ". . . . ." },
    { title: "_ . _ . ." },
  ],
]);

const alertCorrect = ref(false);
const alertIncorrect = ref(false);
const quizIndex = ref(0);
const answerList = [
  ". _ _ . .",
  "_ . _ . .",
  "_ _ . . .",
  ". . . . .",
  "_________",
];

const checkAnswer = (answer: string) => {
  if (answer === answerList[quizIndex.value]) {
    alertCorrect.value = true;
    setTimeout(() => {
      alertCorrect.value = false;
    }, 2000);
  } else {
    alertIncorrect.value = true;
    setTimeout(() => {
      alertIncorrect.value = false;
    }, 2000);
  }

  updateIndex();
};

const updateIndex = () => {
  if (quizIndex.value >= 4) {
    setTimeout(() => {
      router.push("/hint2");
    }, 1500);
  } else {
    quizIndex.value++;
  }
};

const audioRef = ref<HTMLAudioElement | null>(null);

const audioSources = [
  "/sounds/moss1.wav",
  "/sounds/moss2.wav",
  "/sounds/moss3.wav",
  "/sounds/moss4.wav",
  "/sounds/moss5.wav",
];

const playSound = () => {
  if (audioRef.value) {
    audioRef.value.currentTime = 0;
    audioRef.value.play();
  }
};
</script>

<style lang="scss">
.gamepanel {
  height: 80vh;
  border-radius: 5px;
  background: #ffffff77;
}
.playsound{
  background:#a88650;
  border-radius: 52px;
}
</style>
