<template>
  <div id="app">
    <button @click="showModal = true">toggle</button>
    <my-modal v-show="showModal"  @go="go" @closeModal="closeModal">
      <template #modalMessage="id">
        <p>{{id.data}}Lorem ipsum dolor sit amet consectetur adipisicing elit. Quis, itaque fugiat ut illum soluta autem reprehenderit tempora at ex eius?</p>
      </template>
    </my-modal>
  </div>
</template>

<script>
import MyModal from "./components/MyModal";
export default {
  data() {
    return {
      showModal: false
    };
  },
  name: "App",
  methods: {
    closeModal() {
      this.showModal = false;
    },
    go() {
      this.showModal = false;
      console.log("自定义事件");
    }
  },
  components: {
    MyModal
  }
};
</script>

<style>
</style>
