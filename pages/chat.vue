<template>
  <h2>Chat Page {{ user.name }}</h2>
</template>

<script>
import { mapState } from "vuex";

export default {
  middleware: ["chat"],
  head() {
    return {
      title: `Комната ${this.user.room}`,
    };
  },
  computed: mapState(["user"]),
};
</script>

<style>
</style>