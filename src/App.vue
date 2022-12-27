<script setup>
import { onMounted, ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue'
import quizPage from './components/quizPage.vue'


const questionPic = ref([
  {
    title: 'Fil Marsyal', img: '../public/Fil_Marsyal_Darat.png',
  },
  {
    title: 'Jeneral', img: '../public/Jeneral_Darat.png',
  },
  {
    title: 'Leftenan Jeneral', img: '../public/Leftenan_Jeneral_Darat.png',
  },
  {
    title: 'Mejar Jeneral', img: '../public/Mejar_Jeneral_Darat.png',
  },
  {
    title: 'Brigadier Jeneral', img: '../public/Brigadier_Jeneral_Darat.png',
  },
  {
    title: 'Kolonel', img: '../public/Kolonel_Darat.png',
  },
  {
    title: 'Leftenan Kolonel', img: '../public/Leftenan_Kolonel_Darat.png',
  },
  {
    title: 'Mejar', img: '../public/Mejar_Darat.png',
  },
  {
    title: 'Kapten', img: '../public/Kapten_Darat.png',
  },
  {
    title: 'Leftenan', img: '../public/Leftenan_Darat.png',
  },
  {
    title: 'Leftenan Muda', img: '../public/Leftenan_Muda_Darat.png',
  },

  {
    title: 'Mejar', img: '../public/Mejar_Darat.png',
  },
]);

const picRes = ref('')
const titleRes = ref('')
onMounted(() => {
  randomPick()
})

function randomPick() {
  const random = Math.floor(Math.random() * questionPic.value.length);
  picRes.value = new URL(questionPic.value[random].img, import.meta.url).href
  titleRes.value = questionPic.value[random].title
}


</script>

<template>

  <img v-if="picRes" :src="picRes" class="logo" alt="rank" />
  <quizPage :title="titleRes" />
</template>

<style scoped>
.logo {
  height: 20em;
  margin-left: auto;
  margin-right: auto;
  padding: 1.5em;
  will-change: filter;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
