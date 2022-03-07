<template>
  <section class="pt-2">
    <nuxt-link to="/" class="p-3">
      <b-icon icon="box-arrow-left" scale="2"></b-icon>
    </nuxt-link>
    <section class="container">
      <div class="text-2xl">やり直しの中学数学</div>
      <div class="">中学の数学から分かりやすく学ぶ</div>
      <section class="mh-80">
        <table class="table table-sm mt-2">
          <tr v-for="tr in tableData" :key="tr.chapterId">
            <!-- <th>{{ tr.chapterId }}</th> -->
            <td>
              <nuxt-link to="page"> {{ tr.chapterName }}</nuxt-link>
            </td>
            <td class="text-right col-2">
              {{ tr.status }}<span v-show="tr.status">点</span>
            </td>
            <td class="text-right col-2">{{ tr.date }}</td>
          </tr>
        </table>
      </section>
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
