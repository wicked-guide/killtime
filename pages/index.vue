<template>
  <section>
    <b-form-input
      size="sm"
      type="search"
      v-model="search"
      placeholder="Search"
      class="w-25 mb-2"
    ></b-form-input
    >{{ search }}
    <section class="grid">
      <div
        v-for="b in search_books"
        :key="b.book_id"
        class="bg-white border-2 p-1"
      >
        <span v-for="tag in b.tag" :key="tag">
          <b-badge variant="secondary" class="mr-1">{{ tag }}</b-badge></span
        >
        <div class="h4">{{ b.book_name }}</div>

        <div>{{ b.caption }}</div>
      </div>
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
  grid-template-columns: repeat(auto-fit, minmax(200px, 300px));
  grid-gap: 0.5rem;
}
</style>
