<script setup>
  import question from './question.json'; 
  import { ref } from 'vue';

  const ansFlg = ref(false);
  const viewCorrect = () => {
    ansFlg.value = true;
  }
 
  const qaNumber = ref(0);
  const next = () => {
    let num = Math.floor(Math.random() * question.qa.length);
    if (num === qaNumber.value) {
      num = Math.floor(Math.random() * question.qa.length);
    }
    qaNumber.value = num;
    ansFlg.value = false;
  }

</script>

<template>
  <div>
    <h1>応用技術者試験学習用APP</h1>
    <!-- 問題ページ -->
    <div>
      <p>問題：{{ question.qa[qaNumber].q }}</p>
      <p v-show="ansFlg">正解：{{ question.qa[qaNumber].a }}</p>
      <button @click="viewCorrect()">正解を見る</button>
    </div>
    <!-- 次へボタン -->
    <button @click="next()">次へ</button>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
