<template>
  <section class="pt-2">
    <nuxt-link to="/" class="p-3">
      <b-icon icon="box-arrow-left" scale="2"></b-icon>
    </nuxt-link>
    <section class="container border p-2">
      <table>
        <tr>
          <td rowspan="2" class="p-2">
            <b-icon icon="person-fill" scale="2"></b-icon>
          </td>
          <td><b>きっと明日はがんばる</b>さん</td>
        </tr>
        <tr>
          <td>2023/10/10 19:30</td>
        </tr>
      </table>
      <section class="mt-2">
        昔、友達からクイズを出されたのですが解けません
        <div>問題は「この絵は何のことか？」です</div>
        <img src="~/assets/image/mission.jpg" alt="" class="" />
        <div>
          その友達は既に引っ越ししてしまって答えを聞けず、ずっとモヤモヤしています
        </div>
        <div>助けてください</div>
      </section>
    </section>

    <section class="text-center">
      <div class="btn btn-info mt-2 mx-auto">回答する</div>
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
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-gap: 0.5rem;
}
</style>
