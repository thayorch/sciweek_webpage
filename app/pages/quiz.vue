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
    <Incorrect :quizIndex="quizIndex" pages="quiz" />
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
    { title: "โคนัน" },
    { title: "ลูฟี่" },
    { title: "โนบิตะ" },
    { title: "ชินจัง" },
  ],
  [
    { title: "โดราเอม่อน" },
    { title: "โนบิตะ" },
    { title: "ชิซูกะ" },
    { title: "ไจแอ้น" },
  ],
  [
    { title: "หมีพู" },
    { title: "หมีเนย" },
    { title: "ปิกกาจู" },
    { title: "โดราเอม่อน" },
  ],
  [
    { title: "คุโรมิ" },
    { title: "มายเมโลดี้" },
    { title: "ชินจัง" },
    { title: "ปิกกาจู" },
  ],
  [
    { title: "แคร์แบร์" },
    { title: "สปอนจ์บ็อบ" },
    { title: "โดราเอม่อน" },
    { title: "หมีเนย" },
  ],
]);

const imgSource = ref<string[]>([
  "shadow/1.png",
  "shadow/2.png",
  "shadow/3.png",
  "shadow/4.png",
  "shadow/5.png",
]);

const alertCorrect = ref(false);
const alertIncorrect = ref(false);
const quizIndex = ref(0);
const answerList = ["ลูฟี่", "โดราเอม่อน", "ปิกกาจู", "ชินจัง", "สปอนจ์บ็อบ"];

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
  setTimeout(() => {
    updateIndex();
  }, 2100);
};

const updateIndex = () => {
  if (quizIndex.value >= 4) {
    setTimeout(() => {
      router.push("/hint1");
    }, 500);
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
