<script setup>
import { ref } from "vue";
import Intro from "./Intro.vue";
import Playground from "./Playground.vue";

const quizDuration = 30;
const QuizQuestionCount = 5;

const gameState = ref("intro");

const changeGameState = (state) => {
  gameState.value = state;
};
</script>

<template>
  <div>
    <Intro
      v-if="gameState == 'intro'"
      :quiz-duration="quizDuration"
      :quiz-questions-cnt="QuizQuestionCount"
      @change-game-state="changeGameState"
    />
    <Playground
      v-if="gameState == 'play' || gameState == 'finished'"
      :game-state="gameState"
      :quiz-duration="quizDuration"
      :quiz-questions-cnt="QuizQuestionCount"
      @change-game-state="changeGameState"
    />
  </div>
</template>

<style scoped></style>
