<template>
  <v-dialog
    v-model="alertCorrect"
    scrollable
    persistent
    :overlay="false"
    max-width="500px"
    transition="dialog-transition"
    class="animate__animated animate__fadeIn animate__shakeY mx-auto"
  >
    <Correct :quizIndex="quizIndex" pages="quiz" />
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
    <Incorrect :quizIndex="quizIndex" pages="quiz"/>
  </v-dialog>

  <!-- <v-btn color="success" @click="alertCorrect = !alertCorrect">check</v-btn> -->
  <!-- <v-btn color="error" @click="alertIncorrect = !alertIncorrect">check</v-btn> -->

  <v-container class="animate__animated animate__fadeIn animate__shakeY">
    <h1 class="text-center text-white">Quiz {{ quizIndex + 1 }} / 5</h1>

    <div class="mt-8 gamepanel mx-auto text-center">
      <h1 class="text-center text-white">Guess the shadow</h1>
      <v-img
        :src="imgSource[quizIndex]"
        class="ma-2"
        height="250"
        alt="images"
      />

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
              width="100%"
              height="55"
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
  { title: "Conan"},
  { title: "Luffy"},
  { title: "Gojo"},
  { title: "Goku"},
],
  [
  { title: "CSCMU"},
  { title: "DSCMU"},
  { title: "SCICMU"},
  { title: "HUCMU"},
],
  [
  { title: "CSCMU"},
  { title: "DSCMU"},
  { title: "SCICMU"},
  { title: "HUCMU"},
],
  [ 
  { title: "Conan"},
  { title: "Luffy"},
  { title: "Gojo"},
  { title: "Goku"},
],
  [
  { title: ""},
  { title: ""},
  { title: ""},
  { title: ""},
],

]

);

const imgSource = ref<string[]>([
  "quiz1/1.jpg",
  "quiz1/2.jpg",
  "quiz1/3.jpg",
  "quiz1/4.jpg",
  "quiz1/5.jpg",
]);

const alertCorrect = ref(false);
const alertIncorrect = ref(false);
const quizIndex = ref(0);
const answerList = ["Conan", "CSCMU", "DSCMU", "Luffy", ""];

const checkAnswer = (answer: string) => {
  if (answer === answerList[quizIndex.value]) {
    alertCorrect.value = true;
    setTimeout(() => {
      alertCorrect.value = false;
    }, 1000);
  } else {
    alertIncorrect.value = true;
    setTimeout(() => {
      alertIncorrect.value = false;
    }, 1000);
  }

  updateIndex();
};

const updateIndex = () => {
  if (quizIndex.value >= 4) {
    setTimeout(() => {
      router.push("/thanks");
    }, 1500);
  } else {
    quizIndex.value++;
  }
};
</script>

<style lang="scss">
.gamepanel {
  height: 80vh;
  border-radius: 5px;
  background: #ffffff77;
}
</style>
