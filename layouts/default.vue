<template>
  <section class="App">
    <link
      href="https://cdn.jsdelivr.net/npm/tailwindcss@2.1.2/dist/tailwind.min.css"
      rel="stylesheet"
    />
    <!-- ヘッダー -->
    <b-navbar toggleable="md" type="dark" variant="info" class="sticky-top">
      <b-navbar-brand to="/">Wicked Wonder World</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav class="ml-auto">
          <b-nav-item-dropdown text="Lang" right>
            <b-dropdown-item href="#">日本語</b-dropdown-item>
            <b-dropdown-item href="#">English</b-dropdown-item>
          </b-nav-item-dropdown>
          <b-button class="mx-2">ログイン</b-button>
          <b-button>会員登録</b-button>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>

    <!-- メイン -->
    <b-container fluid class="p-0">
      <nuxt />
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
    return {};
  },
};
</script>
