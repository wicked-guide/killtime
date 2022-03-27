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
        <div class="btn btn-info" @click="restrat">リスタート</div>
      </section>
      <!-- カード -->
      <section class="row">
        <!-- 問題カード -->
        <section class="col-6 bg-indigo-100">
          <h4 class="text-center text-2xl font-bold p-2">問題カード</h4>
          <section class="grid">
            <div
              v-for="(q, i) in qcard"
              :key="i"
              class="card border-4"
              :class="{ 'bg-indigo-300 back': !q.qflip, hide: q.qclear }"
              @click="flip(1, i)"
            >
              <span v-show="q.qflip" class="m-auto">{{ q.quiz }}</span>
            </div>
          </section>
          <!-- <div v-for="(q, i) in qcard" :key="i">{{ q.quiz }}</div> -->
        </section>

        <!-- 正解カード -->
        <section class="col-6 bg-yellow-100 pb-2">
          <h4 class="text-center text-2xl font-bold p-2">正解カード</h4>
          <section class="grid">
            <div
              v-for="(a, i) in acard"
              :key="i"
              class="card border-4"
              :class="{ 'bg-yellow-300 back': !a.aflip, hide: a.aclear }"
              @click="flip(2, i)"
            >
              <span v-show="a.aflip" class="m-auto">{{ a.answer }}</span>
            </div>
          </section>
          <!-- <div v-for="(a, i) in acard" :key="i">{{ a.quiz }}</div> -->
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
        {
          quiz: "2x1",
          answer: "2",
          qflip: false,
          aflip: false,
          qclear: false,
          aclear: false,
        },
        {
          quiz: "2x2",
          answer: "4",
          qflip: false,
          aflip: false,
          qclear: false,
          aclear: false,
        },
        {
          quiz: "2x3",
          answer: "6",
          qflip: false,
          aflip: false,
          qclear: false,
          aclear: false,
        },
        {
          quiz: "2x4",
          answer: "8",
          qflip: false,
          aflip: false,
          qclear: false,
          aclear: false,
        },
        {
          quiz: "2x5",
          answer: "10",
          qflip: false,
          aflip: false,
          qclear: false,
          aclear: false,
        },
        {
          quiz: "2x6",
          answer: "12",
          qflip: false,
          aflip: false,
          qclear: false,
          aclear: false,
        },
        {
          quiz: "2x7",
          answer: "14",
          qflip: false,
          aflip: false,
          qclear: false,
          aclear: false,
        },
        {
          quiz: "2x8",
          answer: "16",
          qflip: false,
          aflip: false,
          qclear: false,
          aclear: false,
        },
        {
          quiz: "2x9",
          answer: "18",
          qflip: false,
          aflip: false,
          qclear: false,
          aclear: false,
        },
      ],
      qcard: [],
      acard: [],
      selectQ: "",
      selectA: "",
      indexQ: null,
      indexA: null,
    };
  },
  mounted() {
    this.qshuffle();
    this.ashuffle();
  },
  methods: {
    qshuffle() {
      this.qcard = this.card;
      for (let i = 0; i < this.card.length; i++) {
        let r = Math.floor(Math.random() * (i + 1));
        let tmp = this.qcard[i];
        this.qcard[i] = this.qcard[r];
        this.qcard[r] = tmp;
      }
      return this.qcard;
    },
    ashuffle() {
      this.acard = this.card;
      for (let n = 0; n < this.acard.length; n++) {
        let r = Math.floor(Math.random() * (n + 1));
        let tmp = this.acard[n];
        this.acard[n] = this.acard[r];
        this.acard[r] = tmp;
      }
      return this.acard;
    },
    flip(n, i) {
      // console.log(i);
      switch (n) {
        // 問題カード
        case 1:
          if (this.selectQ) {
            break;
          }
          this.indexQ = i;
          this.card[i].qflip = !this.card[i].qflip;
          this.selectQ = this.card[i].answer;
          break;
        // 解答カード
        case 2:
          if (this.selectA) {
            break;
          }
          this.indexA = i;
          this.card[i].aflip = !this.card[i].aflip;
          this.selectA = this.card[i].answer;
          break;
      }
      const flip = new Audio(flip);
      flip.play();
      if (this.selectQ && this.selectA) {
        setTimeout(() => {
          this.check();
        }, 700);
      }
    },
    check() {
      if (this.selectQ == this.selectA) {
        this.card[this.indexQ].qclear = true;
        this.card[this.indexA].aclear = true;
      }
      this.reset();
    },
    reset() {
      this.selectQ = "";
      this.selectA = "";
      this.indexQ = null;
      this.indexA = null;
      this.card.forEach((element) => {
        element.qflip = false;
        element.aflip = false;
      });
    },
    restrat() {
      this.selectQ = "";
      this.selectA = "";
      this.indexQ = null;
      this.indexA = null;
      this.card.forEach((element) => {
        element.qflip = false;
        element.aflip = false;
        element.qclear = false;
        element.aclear = false;
      });
      this.qshuffle();
      this.ashuffle();
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

/* hide */
.hide {
  visibility: hidden;
}
</style>
