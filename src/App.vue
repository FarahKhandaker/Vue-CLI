<template>
  <div>
    <h1>{{ title }}</h1>
    <p>Welcome</p>
    <teleport to=".modals" v-if="showModal">
      <!-- ! props -->
      <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal" /> -->
      <!-- ! slots -->
      <Modal theme="sale" @close="toggleModal">
        <template v-slot:links>
          <a href="#">sign up</a>
          <a href="#">more info</a>
        </template>
        <h1>Ninja Givaway</h1>
        <p>Grab your ninja swag for half price!</p>
      </Modal>
    </teleport>

    <teleport to=".modals" v-if="showModalTwo">
      <Modal @close="toggleModalTwo">

        <h1>Ninja Givaway 2</h1>
        <p>Grab your ninja swag for half price 2!</p>
      </Modal>
    </teleport>
    <button @click.alt="toggleModal">Open modal (alt)</button>
    <button @click="toggleModalTwo">Open New Modal</button>
    <!-- <template>
      <div>
        <h1>{{ title }}</h1>
        <div v-if="showModalTwo">
          <Modal theme="newSale">
            <h1>Ninja Givaway 2</h1>
            <p>Grab your ninja swag for half price 2!</p>
          </Modal>
        </div>
        <button @click.shift="toggleModalTwo">Open New Modal (shift)</button>
      </div>
    </template> -->
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My First Vue App :)",
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    // handleClick() {
    //   console.log(this.$refs.name)
    //   this.$refs.name.classList.add('active')
    //   this.$refs.name.focus()
    // }
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
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
