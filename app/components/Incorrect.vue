<script setup lang="ts">
const props = defineProps<{
  quizIndex: number
  pages: string
}>()

const ismossPage = ref(props.pages === "moss")

const quizSource = [
  "answer/1.png",
  "answer/2.png",
  "answer/3.png",
  "answer/4.png",
  "answer/5.png",
]

const mossSource = [
  ". _ _ . .",
  "_ . _ . .",
  "_ _ . . .",
  ". . . . .",
  "_________",
];

const vialSource = [
  "vials/A.jpg",
  "vials/B.jpg",
  "vials/C.jpg",
  "vials/D.jpg",
  "vials/E.jpg",
  "vials/F.jpg",
]

const answerImage = computed(() => {
  if (props.pages === "quiz") {
    return quizSource[props.quizIndex]
  } else if (props.pages === "vial") {
    return vialSource[props.quizIndex]
  }
  return ""
})

const mossPattern = computed(() => {
  if (props.pages === "moss") {
    return mossSource[props.quizIndex-1]
  }
  return ""
})
</script>

<template>
  <v-container class="pa-md-12 text-center">
    <v-alert
      class="mx-auto mb-4"
      icon="$error"
      color="error"
      max-width="700"
      rounded="lg"
      title="Incorrect"
    />
    
    <v-card v-if="ismossPage" class="mx-auto mb-4 pa-4" max-width="300">
      <div class="text-h4 font-mono">
        {{ mossPattern }}
      </div>
    </v-card>
    
    <v-img 
      v-if="!ismossPage" 
      :src="answerImage" 
      max-width="300" 
      height="360" 
      class="mx-auto" 
    />
  </v-container>
</template>