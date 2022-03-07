<template>
  <section class="pt-2">
    <nuxt-link to="/" class="p-3">
      <b-icon icon="box-arrow-left" scale="2"></b-icon>
    </nuxt-link>
    <section class="container">
      <div class="text-2xl">やり直しの中学数学</div>
      <div class="">中学の数学から分かりやすく学ぶ</div>
      <div class="">式の計算</div>
      <!-- 動画 -->
      <iframe
        width="560"
        height="315"
        src="https://www.youtube.com/embed/b2_OORXpNlM"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      ></iframe>
      <!-- テキスト -->
      <section>
        <h3 class="text-2xl">式の種類</h3>
        <table class="table table-sm w-auto">
          <tr>
            <td class="">単項式</td>
            <td>
              文字の項が１つだけの式
              <div>例）2x+5=9</div>
            </td>
          </tr>
          <tr>
            <td>多項式</td>
            <td>
              文字の項が２つ以上ある式
              <div>例）2x+5y=9</div>
            </td>
          </tr>
          <tr>
            <td>同類項</td>
            <td>
              多項式で、文字の部分が同じ項のこと
              <div>例）2x+5y=3x+3y</div>
            </td>
          </tr>
        </table>
      </section>
      <!-- 問題 -->
    </section>
  </section>
</template>

<script>
import Vue from "vue";
import db from "../assets/db.json";

export default Vue.extend({
  data() {
    return {
      tableData: db.chapter,
    };
  },
});
</script>
