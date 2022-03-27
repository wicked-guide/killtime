<template>
  <section class="pt-2">
    <nuxt-link to="/" class="p-3">
      <b-icon icon="box-arrow-left" scale="2"></b-icon>
    </nuxt-link>
    <section class="container">
      <div class="text-2xl">偉人年表</div>
      <!-- タグ検索 -->
      <section class="mb-1 row">
        <!-- <section class="col-6">
          <label for="tags">タグ検索</label>
          <b-form-tags
            input-id="tags"
            placeholder="タグ"
            v-model="tags"
          ></b-form-tags>
        </section> -->
        <section class="col-6">
          <input
            type="search"
            v-model="search"
            placeholder="検索"
            class="form-control"
          />
        </section>
        <!-- <section class="col-6">
          <b-form-checkbox-group
            id="checkbox"
            v-model="selectTag"
            :options="tags"
            :aria-describedby="ariaDescribedby"
            variant="info"
          ></b-form-checkbox-group>
        </section> -->
      </section>
      <!-- テーブル -->
      <section class="mh-80">
        <table class="table table-sm">
          <thead class="table-info sticky-top">
            <th>年代</th>
            <!-- <th>種別</th> -->
            <th>人物</th>
            <th>解説</th>
          </thead>
          <tr v-for="(tr, index) in searchTable" :key="index">
            <td>{{ tr.from }}</td>
            <!-- <td>
              <b-badge v-for="t in tr.tag" :key="t">{{ t }}</b-badge>
            </td> -->
            <td>
              {{ tr.person }}
            </td>
            <td>
              <b-badge v-for="t in tr.tag" :key="t" class="mr-1">{{
                t
              }}</b-badge>
              <div>{{ tr.comment }}</div>
              <div class="text-sm text-gray-500">{{ tr.note }}</div>
            </td>
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
      table: db.chronology,
      selectTag: [],
      tags: [
        { text: "西洋哲学", value: "西洋哲学" },
        { text: "東洋哲学", value: "東洋哲学" },
        { text: "数学", value: "数学" },
        { text: "経済学", value: "経済学" },
      ],
      search: "",
    };
  },
  mounted() {},
  methods: {},
  computed: {
    searchTable() {
      return this.table.filter((s) => {
        return (
          s.person.includes(this.search) ||
          s.comment.includes(this.search) ||
          s.note.includes(this.search) ||
          s.tag.includes(this.search)
        );
      });
    },
  },
});
</script>

<style>
.chronology th,
.chronology td {
  padding: 0 0.5rem;
}
</style>
