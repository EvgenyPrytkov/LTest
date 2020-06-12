<template>
  <div class="row">
    <div
      class="col-xs-12 col-sm-6 col-md-4 col-lg-4 mypadding"
      v-for="n in 6"
      :key="n"
    >
      <div class="mycard"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "my-body",
};
</script>

<style scoped>
.row {
  padding: 10px !important;
}
.mypadding {
  padding: 10px !important;
}

.mycard {
  background-color: gray;
  height: 200px;
}
</style>
