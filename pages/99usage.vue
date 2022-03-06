<template>
  <section>
    <div>
      <b-button variant="primary">Primary</b-button>
      <b-button variant="secondary">Secondary</b-button>
      <b-button variant="success">Success</b-button>
      <b-button variant="danger">Danger</b-button>
      <b-button variant="warning">Warning</b-button>
      <b-button variant="info">Info</b-button>
      <b-button variant="light">Light</b-button>
      <b-button variant="dark">Dark</b-button>
      <br />
      <b-button variant="softblue">softblue</b-button>
      <b-button variant="softgreen">softgreen</b-button>
      <b-button variant="softyellow">softyellow</b-button>
      <b-button variant="softred">softred</b-button>
      <br />
      <b-button variant="pos">pos</b-button>
      <b-button variant="neg">neg</b-button>
      <br />
      <b-button variant="pos">pos</b-button>
      <b-button variant="softyellow">neg</b-button>
    </div>
  </section>
</template>

<script>
import Vue from "vue";
import dbJson from "../assets/db.json";

export default Vue.extend({
  layout: "menu",
  data() {
    return {
      db: dbJson,
    };
  },
  mounted() {},
  methods: {},
});
</script>
