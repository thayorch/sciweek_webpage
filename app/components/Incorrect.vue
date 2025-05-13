<script setup lang="ts">
const props = defineProps<{
  quizIndex: number
  pages: string
}>()

const answerSource = [
  "answer/1.png",
  "answer/2.png",
  "answer/3.png",
  "answer/4.png",
  "answer/5.png",
]

const answerImage = computed(() =>
  props.pages === "quiz"
    ? answerSource[props.quizIndex]
    : "answer/roll-safe-meme-1.jpg"
)
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
    <v-img :src="answerImage" max-width="300" height="360" class="mx-auto" />
  </v-container>
</template>
