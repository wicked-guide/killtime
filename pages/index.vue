<template>
  <section class="">
    <!-- layout -->
    <b-container fluid class="bv-example-row">
      <b-row class="py-3">
        <!-- main -->
        <b-col md="8">
          <b-form-input
            size="sm"
            type="search"
            v-model="search"
            placeholder="Search"
            class="mb-2"
          ></b-form-input>
          <section class="grid">
            <nuxt-link
              to="chapter"
              v-for="b in search_books"
              :key="b.book_id"
              class="bg-white border-2 p-1"
            >
              <span v-for="(tag, index) in b.tag" :key="index">
                <b-badge variant="secondary" class="mr-1">{{
                  tag
                }}</b-badge></span
              >
              <div class="h4">{{ b.book_name }}</div>

              <div>{{ b.caption }}</div>
            </nuxt-link>
          </section>
        </b-col>
        <!-- sub -->
        <b-col md="4" class="w-md right-0 mh-100 overflow-auto pb-5">
          <!-- game -->
          <section class="bg-green-100 p-2 rounded-2xl">
            <nuxt-link to="game">
              <div class="text-2xl">ミニゲーム</div>
              <img src="~/assets/image/gameicon.png" alt=""
            /></nuxt-link>
          </section>

          <!-- ちょっとした情報 -->
          <section class="bg-green-100 mt-3 p-2 rounded-2xl">
            <div class="text-2xl">ちょっとした情報</div>
            <ul>
              <li
                v-for="(i, index) in info"
                :key="index"
                class="bg-white p-1 mb-1 rounded-tr-2xl"
              >
                <nuxt-link to="info">
                  <div class="text-indigo-700">{{ i.title }}</div>
                  <div class="text-gray-400 text-md-right">{{ i.date }}</div>
                </nuxt-link>
              </li>
            </ul>
          </section>

          <!-- ミッション -->
          <section class="bg-green-100 mt-3 p-2 rounded-2xl">
            <div class="text-2xl">クエスト</div>
            <ul>
              <li class="bg-white p-1 mb-1 rounded-tr-2xl">
                <nuxt-link to="mission">
                  <div class="text-indigo-700">誰か助けて！</div>
                  <div class="text-gray-400 text-md-right">2023/10/10</div>
                </nuxt-link>
              </li>
              <li class="bg-white p-1 mb-1 rounded-tr-2xl">
                <nuxt-link to="mission">
                  <div class="text-indigo-700">
                    地球から月までの距離を、自分で実際に測ってみたい
                  </div>
                  <div class="text-gray-400 text-md-right">2023/9/17</div>
                </nuxt-link>
              </li>
            </ul>
          </section>

          <!-- 学問紹介 -->
          <section class="bg-green-100 mt-3 p-2 rounded-2xl mb-5">
            <div class="text-2xl">やりたいこと探し</div>
            <section class="bg-blue-200 rounded-tr-2xl p-1">
              <div class="text-center">進学：学部選び編</div>
              <ul class="px-1">
                <li class="bg-white p-1 mb-1 rounded-tr-2xl">
                  <nuxt-link to="mission">
                    <div class="text-indigo-700">謎の学問？哲学部</div>
                    <div class="text-gray-400 text-md-right">2023/9/10</div>
                  </nuxt-link>
                </li>
                <li class="bg-white p-1 mb-1 rounded-tr-2xl">
                  <nuxt-link to="mission">
                    <div class="text-indigo-700">実験漬けの毎日　科学部</div>
                    <div class="text-gray-400 text-md-right">2023/9/10</div>
                  </nuxt-link>
                </li>
              </ul>
            </section>
            <section class="bg-blue-200 rounded-tr-2xl mt-2 p-1">
              <div class="text-center">就職：仕事選び編</div>
              <ul class="px-1">
                <li class="bg-white rounded-tr-2xl p-1 mb-1">
                  <nuxt-link to="mission">
                    <div class="text-indigo-700">手堅い人気！公務員の実態</div>
                    <div class="text-gray-400 text-md-right">2023/8/12</div>
                  </nuxt-link>
                </li>
              </ul>
            </section>
          </section>
        </b-col>
      </b-row>
    </b-container>
  </section>
</template>

<script>
import Vue from "vue";
import db from "../assets/db.json";

export default Vue.extend({
  data() {
    return {
      book: db.book,
      info: db.info,
      search: "",
    };
  },
  mounted() {},
  methods: {},
  computed: {
    search_books() {
      return this.book.filter((book) => {
        return (
          book.book_name.includes(this.search) ||
          book.caption.includes(this.search) ||
          book.tag.includes(this.search)
        );
      });
    },
  },
});
</script>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-gap: 0.5rem;
}
</style>
