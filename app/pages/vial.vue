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
    <Correct :quizIndex="currentQuestionIndex" pages="vial" />
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
    <Incorrect :quizIndex="currentQuestionIndex" pages="vial" />
  </v-dialog>
  <v-container class="animate__animated animate__fadeIn animate__shakeY">
    <h1 class="text-center text-white">Quiz {{ quizIndex + 1 }} / 3</h1>
    <div class="mt-8 gamepanel mx-auto text-center">
      <h1 class="text-center text-white">Guess the Vial</h1>
      <v-img :src="imgSource" class="ma-2" height="250" alt="images" />
      <div class="font-weight-bold text-h6 ma-3 bg-white">{{ currentHint.content }}</div>
      <div class="option ma-8">
        <v-row>
          <v-col
            v-for="(data, index) in optionData"
            :key="index"
            cols="4"
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
  { title: "A" },
  { title: "B" },
  { title: "C" },
  { title: "D" },
  { title: "E" },
  { title: "F" },
]);

const allAnswers = ["A", "B", "C", "D", "E", "F"];
const allHints = [
  {
    content: `น้ำยาสลับร่าง อยู่ในขวดที่มีสัญลักษณ์บนฉลาก และฝาไม่เป็นไม้
สีของน้ำยาในขวดที่ถูกต้องคือสีที่ ใสและดูมีพลังเวท
ขวดที่ถูกต้อง สูงกว่าขวดอื่น และมีฝาทรงพิเศษ`,
  },
  {
    content: `สิ่งไม่มีฉลาก บางครั้งอาจซ่อนความลับที่สุดเอาไว้
กลมดั่งร่างกายมนุษย์ แปรเปลี่ยนได้ตามใจปรารถนา
สีเข้ม ลึก ลึกลับ เหมือนตัวตนที่ยังไม่ถูกเปิดเผย`,
  },
  {
    content: `การเปลี่ยนร่าง ไม่ได้เปลี่ยนเพียงรูปลักษณ์ แต่อาจเปลี่ยนจากหัวใจ
สีอ่อนเย็น เหมือนความรู้สึกที่ไม่แน่นอน อาจเป็นเธอ หรือเป็นฉัน
รูปทรงมั่นคง แต่ผลลัพธ์กลับไม่แน่นอนเลย`,
  },
  {
    content: `น้ำยาสลับร่างอยู่ในขวดที่ มีฝาเกลียวโลหะ และดู เหมือนหลอดทดลอง
ขวดที่มี สีของน้ำยาเป็นสีเขียวหรือชมพู ไม่ใช่ขวดที่ถูกต้อง
น้ำยาสลับร่างอยู่ในขวดที่ มีสัญลักษณ์ที่สื่อถึง "การเปลี่ยนแปลง" หรือ "การเคลื่อนไหว"`,
  },
  {
    content: `บางครั้งคำตอบที่ใช่…ก็อยู่ในคำถามนั่นแหละ
สีที่ไม่เหมือนใคร มักซ่อนพลังที่ไม่มีใครคาดถึง
ขวดนี้ดูไม่แน่ใจ...แต่อาจแน่ใจที่สุดในบรรดาทุกขวด`,
  },
  {
    content: `ดวงตาไม่เคยโกหก
เปลี่ยนได้ทุกสิ่ง หากมองให้ลึกพอ
สีเข้มดั่งเลือด แต่ซ่อนพลังของตัวตนอีกคนไว้ภายใน`,
  },
];

// สุ่มเลือก 3 ข้อจาก 6 ข้อ
const getRandomQuestions = () => {
  const indices = [0, 1, 2, 3, 4, 5];
  const shuffled = indices.sort(() => Math.random() - 0.5);
  return shuffled.slice(0, 3);
};

const randomIndices = ref(getRandomQuestions());
const quizIndex = ref(0);
const alertCorrect = ref(false);
const alertIncorrect = ref(false);
const imgSource = "vials/viallist.png";

// ใช้ computed เพื่อให้ได้ข้อมูลปัจจุบัน
const currentQuestionIndex = computed(() => randomIndices.value[quizIndex.value]);
const currentHint = computed(() => allHints[currentQuestionIndex.value]);
const currentAnswer = computed(() => allAnswers[currentQuestionIndex.value]);

const checkAnswer = (answer: string) => {
  if (answer === currentAnswer.value) {
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
  setTimeout(() => {
    updateIndex();
  }, 1200);
};

const updateIndex = () => {
  if (quizIndex.value >= 2) { // 3 ข้อ คือ index 0, 1, 2
    setTimeout(() => {
      router.push("/hint3");
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