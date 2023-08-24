<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1>{{ title }}</h1>
  <input type="text" ref="name">
  <div>
    <button class="openModal" @click="handleClick">Click Me!</button>
    <button class="openModal" @click="toggleModal">open modal</button>
    <button class="openModal" @click="toggleModal2">open modal 2</button>
  </div>
  <Modal v-if="displayModal" @close="toggleModal"/>
  <Modal v-if="displayModal2" @close="toggleModal2">
    I'm better than Modal 1
  </Modal>
</template>

<script>
import Modal from "./components/Modal.vue"

export default {
  data() {
    return {
      title: "My First Vue App :)",
      displayModal: false,
      displayModal2: false
    }
  },
  methods: {
    handleClick() {
      this.$refs.name.focus()
    },
    toggleModal() {
      this.displayModal = !this.displayModal
    },
    toggleModal2() {
      this.displayModal2 = !this.displayModal2
    }
  },
  components: {
    Modal
  }
}
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
.openModal {
  display: inline-block;
  background-color: transparent;
  padding: 10px;
  margin: 10px;
  border: 1px solid black;
  border-radius: 5px;
}
</style>
