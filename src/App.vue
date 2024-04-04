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
    <!-- 問題ページ -->
    <div class="inner-width">
      <h1>応用技術者試験学習用APP</h1>
      <div class="q">
        <p>問題：{{ question.qa[qaNumber].q }}</p>
      </div>
      <div class="a">
        <p v-show="ansFlg">正解：{{ question.qa[qaNumber].a }}</p>
      </div>
      <button @click="viewCorrect()">正解を見る</button>
      
      <!-- 次へボタン -->
      <button @click="next()">次へ</button>
    </div>

  </div>
</template>

<style>
.inner-width {
  width:350px;
  margin: 0 auto;
}

.q {
  border: 2px solid #ccc;
  border-radius: 5px;
  padding:30px;
  margin: 1rem 0;
  font-size: 1.4rem;
  line-height: 1.7;

}

.a {
  background: #c8e3ff;
  padding: 30px;
  border-radius: 5px;
  font-size: 1.4rem;
  line-height: 1.7;
}

button {
  background: rgb(118, 216, 118);
  border: none;
  border-radius: 3px;
  padding: 15px 25px;
  margin-right: 5px;
  margin-top: 10px;
}
</style>
