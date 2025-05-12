<script setup lang="ts">
import { ref, computed } from 'vue'
import { defineProps } from 'vue'

const props = defineProps<{
  quizIndex: number
}>()

const answerSource = ref<string[]>([
  "quiz1/ans/1.jpg",
  "quiz1/ans/2.jpg",
  "quiz1/ans/3.jpg",
  "quiz1/ans/4.jpg",
  "quiz1/ans/5.jpg",
])

const answerImage = computed(() => answerSource.value[props.quizIndex])
</script>

<template>
  <v-container class="pa-md-12 text-center">
    <v-alert
      class="mx-auto mb-4"
      icon="$success"
      color="success"
      max-width="700"
      rounded="lg"
      title="Correct"
    />
    <v-img :src="answerImage" max-width="300" class="mx-auto" />
  </v-container>
</template>
