<template>
  <section class="pt-2">
    <nuxt-link to="/" class="p-3">
      <b-icon icon="box-arrow-left" scale="2"></b-icon>
    </nuxt-link>
    <!-- <img src="~/assets/image/reversi.jpg" alt="" class="m-auto" /> -->

    <!-- ゲームエリア -->
    <canvas id="canvas" class="d-block m-auto border-4"></canvas>

    <!-- デバッグエリア -->
    <section class="container grid">
      <b>canvas</b>
      <div>{{ canvas }}</div>
      <b>ctx</b>
      <div>{{ ctx }}</div>
      <b>width</b>
      <div><input type="number" v-model="width" /></div>
      <b>height</b>
      <div><input type="number" v-model="height" /></div>
    </section>
  </section>
</template>

<script>
import Vue from "vue";
import db from "../assets/db.json";

export default Vue.extend({
  data() {
    return {
      db: db,
      // キャンバス
      canvas: null,
      ctx: null,
      width: 360,
      height: 500,
      // アイテム
      block: {
        constructor(x, y, w, h, col, storke) {
          this.x = x;
          this.y = y;
          this.w = w;
          this.h = h;
          this.col = col;
          this.storke = storke;
        },
        draw() {
          drawRect(this.x, this.y, this.w, this.h, this.col, this.storke);
        },
      },
      paddle: {
        constructor(x, y, w, h, col, storke) {
          this.x = x;
          this.y = y;
          this.w = w;
          this.h = h;
          this.col = col;
          this.storke = storke;
        },
      },
      ball: "",
    };
  },
  methods: {
    // 初期化
    init() {
      console.log("init");
      this.canvas = document.getElementById("canvas");
      this.ctx = this.canvas.getContext("2d");
      this.canvas.width = this.width;
      this.canvas.height = this.height;

      this.start();
      this.loop();
    },

    // 背景色
    drawRect(x, y, w, h, col, storke = false) {
      this.ctx.fillStyle = col;
      this.ctx.fillRect(x, y, w, h);
      if (storke) {
        ctx.strokeRect(x, y, w, h);
      }
    },

    //  アイテム読み込み
    start() {
      // this.paddle = new Paddle(width / 2, 480);
      // ball = new Ball();
      // console.log("start");
    },

    // ループ
    loop() {
      console.log("loop");
      this.drawRect(0, 0, this.width, this.height, "gray");
      // requestAnimationFrame(loop);
    },
  },
  mounted() {
    console.log("mounted");
    this.init();
  },
});
</script>

<style>
.grid {
  display: grid;
  grid-template-columns: 1fr 4fr;
}
</style>
