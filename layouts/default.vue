<template>
  <section class="App">
    <link
      href="https://cdn.jsdelivr.net/npm/tailwindcss@2.1.2/dist/tailwind.min.css"
      rel="stylesheet"
    />
    <!-- ヘッダー -->
    <b-navbar toggleable="lg" type="dark" variant="info" class="sticky-top">
      <b-navbar-brand href="#">E-OS</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <!-- <b-navbar-nav>
          <b-nav-item href="#">Link</b-nav-item>
          <b-nav-item href="#" disabled>Disabled</b-nav-item>
        </b-navbar-nav> -->

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input size="sm" placeholder="Search"></b-form-input>
            <b-button size="sm" class="my-2 my-sm-0" type="submit"
              ><b-icon icon="search" aria-hidden="true"></b-icon
            ></b-button>
          </b-nav-form>

          <b-nav-item-dropdown text="Lang" right>
            <b-dropdown-item href="#">日本語</b-dropdown-item>
            <b-dropdown-item href="#">English</b-dropdown-item>
          </b-nav-item-dropdown>

          <b-nav-item-dropdown right>
            <template #button-content> 生徒名○○ </template>
            <b-dropdown-item href="#">個人設定</b-dropdown-item>
            <b-dropdown-item href="#">ログアウト</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>

    <b-container fluid class="bv-example-row">
      <b-row>
        <!-- サイドメニュー -->
        <b-col
          cols="12"
          md="2"
          class="w750 h-100 overflow-y-auto pt-3 bg-green-100"
        >
          <ul class="menu-list">
            <li v-for="item in links" :key="item">
              <NuxtLink :to="item.to" class="text-lg nowrap">
                {{ item.title }}
              </NuxtLink>
            </li>
          </ul>
        </b-col>
        <!-- コンテンツ -->
        <b-col cols="12" md="10" class="ml-auto pt-3"> <nuxt /></b-col>
      </b-row>
    </b-container>
  </section>
</template>

<script lang="ts">
import Vue from "vue";
import { BootstrapVue, BootstrapVueIcons } from "bootstrap-vue";
Vue.use(BootstrapVue);
Vue.use(BootstrapVueIcons);

export default {
  data() {
    return {
      links: [
        {
          title: "使い方",
          to: { name: "99.usage" },
        },
        {
          title: "Home",
          to: { name: "index" },
        },
        {
          title: "教師：メニュー",
          to: { name: "t-menu" },
        },
      ],
    };
  },
};
</script>

<style>
@media screen and (min-width: 750px) {
  .w750 {
    position: fixed;
  }
}
</style>
