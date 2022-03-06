<template>
  <section class="pt-2">
    <nuxt-link to="/" class="p-3">
      <b-icon icon="box-arrow-left" scale="2"></b-icon>
    </nuxt-link>
    <!--  -->
    <section class="container">
      <h3 class="text-2xl border-b-4 mb-2">
        あなたの知らない世界：実は儲かっている駄菓子編
      </h3>
      <article>
        <div>
          昔から、多くの人hが「どうして勉強しなくてはならないのか？」と疑問に感じてきたが、その問いに対する代表的な解答が「<b>ちゃんとした社会人になるため</b>」だろう。
        </div>
        <div>
          しかし、しっかり勉強して良い成績をとれたら、果たして本当に「<b>ちゃんとした社会人</b>」になれるのだろうか？
        </div>
        <ul>
          <li>・売れる商品の作り方</li>
          <li>・効果的な宣伝方法</li>
          <li>・決算書の読み方</li>
        </ul>
        <div>そういった仕事に関することを、学校では全く教えてくれない。</div>
        <div>
          そこで今回は、駄菓子屋を例に挙げて「学校では教えてくれないビジネス入門」として、基本的なことをレクチャーしていこう。
        </div>
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
