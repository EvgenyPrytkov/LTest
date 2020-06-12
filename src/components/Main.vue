<template>
  <div>
    <my-header @showModal="showModal = true"></my-header>
    <my-body></my-body>
    <my-modal v-if="showModal" @close="showModal = false"></my-modal>
  </div>
</template>

<script>
import MyHeader from "./Header";
import MyBody from "./Body";
import MyModal from "./Modal";
export default {
  name: "l-main",
  components: { MyHeader, MyBody, MyModal },
  data() {
    return { showModal: false };
  }
};
</script>

<style></style>
