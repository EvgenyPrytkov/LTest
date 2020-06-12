<template>
  <div>
    <nav class="navbar navbar-default navbar-dark bg-secondary">
      <a class="navbar-brand" href="#">Test Lofty</a>
      <button type="button" class="btn btn-dark" @click="showModal">
        SIGN UP
      </button>
    </nav>
  </div>
</template>

<script>
export default {
  name: "my-header",
  methods: {
    showModal: function() {
      // generate event for showing modal window
      this.$emit("showModal");
    },
  },
};
</script>

<style></style>
