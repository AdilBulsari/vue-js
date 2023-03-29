<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  <h1>{{ title }}</h1>
  <input type="text" ref="name" />
  <button @click="handleClick">Click me</button>
  <!-- <Modal header="Buy Blinds !!" text="Very good for the luxury home" /> -->
  <div v-if="showModal">
    <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal" /> -->
    <Modal @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#"> more info</a>
      </template>
      <h1>My First Vue App :)</h1>
      <p>Very good product for luxurious home</p>
    </Modal>
  </div>

  <div v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>Second Modal</h1>
      <p>I am second modal</p>
    </Modal>
  </div>

  <button @click="toggleModal">Open Modal</button>
  <button @click="toggleModalTwo">Second Modal</button>
</template>

<script>
import Modal from "./components/Modal.vue";
export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "My First Vue App :)",
      header: "Buy Blinds",
      text: "Very good product for luxurious home",
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
