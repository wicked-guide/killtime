<template>
  <section class="pt-2">
    <nuxt-link to="/" class="p-3">
      <b-icon icon="box-arrow-left" scale="2"></b-icon>
    </nuxt-link>
    <!-- ゲームエリア -->
    <section class="container mt-2 border-4">
      <h1 class="text-center text-2xl font-bold">九九で神経衰弱</h1>
      <!-- ヘッダー -->
      <section class="d-flex justify-between">
        <div class="btn btn-info">ステージ</div>
        <div class="m-auto">ポイント：</div>
        <div class="btn btn-info">リスタート</div>
      </section>
      <!-- カード -->
      <section class="row">
        <!-- 問題カード -->

        <section class="col-6 bg-indigo-100">
          <h4 class="text-center text-2xl font-bold p-2">問題カード</h4>
          <section class="grid">
            <div
              v-for="(q, i) in card"
              :key="i"
              class="card border-4"
              :class="{ 'bg-indigo-300 back': !q.qflip }"
              @click="flip(1, i)"
            >
              <span v-show="q.qflip" class="m-auto">{{ q.quiz }}</span>
            </div>
          </section>
        </section>

        <!-- 正解カード -->
        <section class="col-6 bg-yellow-100 pb-2">
          <h4 class="text-center text-2xl font-bold p-2">正解カード</h4>
          <section class="grid">
            <div
              v-for="(a, i) in card"
              :key="i"
              class="card border-4"
              :class="{ 'bg-yellow-300 back': !a.aflip }"
              @click="flip(2, i)"
            >
              <span v-show="a.aflip" class="m-auto">{{ a.answer }}</span>
            </div>
          </section>
        </section>
      </section>
    </section>
  </section>
</template>

<script>
import Vue from "vue";
import db from "../assets/db.json";
import flip from "../assets/sound/flip.mp3";

export default Vue.extend({
  data() {
    return {
      db: db,
      card: [
        { quiz: "2x1", answer: "2", qflip: false, aflip: false },
        { quiz: "2x2", answer: "4", qflip: false, aflip: false },
        { quiz: "2x3", answer: "6", qflip: false, aflip: false },
        { quiz: "2x4", answer: "8", qflip: false, aflip: false },
        { quiz: "2x5", answer: "10", qflip: false, aflip: false },
      ],
    };
  },
  mounted() {},
  methods: {
    flip(n, i) {
      // console.log(i);
      const flip = new Audio(flip);
      flip.play();
      switch (n) {
        case 1:
          this.card[i].qflip = !this.card[i].qflip;
          break;
        case 2:
          this.card[i].aflip = !this.card[i].aflip;
          break;
      }
    },
  },
  computed: {},
});
</script>

<style>
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
  grid-gap: 0.5rem;
}

/* card size */
.card {
  height: 3rem;
  text-align: center;
  cursor: pointer;
  transform: rotateY(0deg);
  transition: transform 0.3s;
}

/* card back */
.back {
  background-size: 60px 55px;
  background-image: radial-gradient(
      transparent 10px,
      #ffffff 20px,
      #ffffff 12px,
      transparent 12px
    ),
    radial-gradient(
      transparent 10px,
      #ffffff 24px,
      #ffffff 12px,
      transparent 24px
    );
  background-position: 0 0, 16px 16px;
  transform: rotateY(180deg);
  transition: transform 0.3s;
}
</style>
