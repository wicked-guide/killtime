<template>
  <section class="pt-2">
    <nuxt-link to="/" class="p-3">
      <b-icon icon="box-arrow-left" scale="2"></b-icon>
    </nuxt-link>
    <!--  -->
    <section class="container">
      <h3 class="text-2xl border-b-4 mb-2">潜入レポート：旨い学食ランキング</h3>
      <article>
        <ul v-for="i in 10" :key="i">
          <li class="border-8 rounded-3xl p-2 mb-2">
            <div class="text-3xl d-flex">
              <div>
                <b-badge variant="info">第{{ i }}位</b-badge>※※学院：〇〇定食
              </div>
              <div class="ml-auto">**円</div>
            </div>
            <div class="row">
              <img src="~/assets/image/lunch.png" alt="" class="col-6" />
              <div class="col-6">
                <p class=""><b>評価ポイント</b></p>
                <p>
                  毎日食べても良い旨さと栄養バランス、そして価格の見事な「丁度よさ！」
                </p>
              </div>
            </div>
          </li>
        </ul>
      </article>
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
      book: db.book,
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
article div {
  margin-bottom: 0.5rem;
}
</style>
