<template>
  <section class="pt-2">
    <nuxt-link to="/" class="p-3">
      <b-icon icon="box-arrow-left" scale="2"></b-icon>
    </nuxt-link>
    <img src="~/assets/image/reversi.jpg" alt="" class="m-auto" />
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
