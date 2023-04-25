<template>
  <div class="modal" v-if="showModal">
    <div class="modal-overlay" @click="closeModal"></div>
    <div class="modal-container">
      <div class="modal-header">
        <h3>{{ card.title }}</h3>
        <button class="close-button" @click="closeModal">X</button>
      </div>
      <p class="author">{{ card.author }}</p>
      <div class="modal-content">
        <div class="modal-slider">
          <img v-for="(image, index) in card.images" :src="image" :key="index" />
        </div>
        <p>{{ card.description }}</p>
        <p>Price: {{ card.price }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    card: {
      type: Object,
      required: true
    },
    showModal: {
      type: Boolean,
      required: true
    }
  },
  methods: {
    closeModal() {
      this.$emit("close-modal");
    }
  }
};
</script>

<style>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 9999;
}
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
}
.modal-container {
  position: relative;
  margin: auto;
  max-width: 600px;
  max-height: 90%;
  overflow: auto;
  background-color: #fff;
  border-radius: 5px;
  padding: 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}
.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.close-button {
  font-size: 30px;
  background-color: transparent;
  border: none;
  cursor: pointer;
}
.author {
  margin-top: -1vw;
}
.modal-content {
  margin-top: 20px;
}
.slider {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}
.slider img {
  max-width: 100%;
  max-height: 300px;
  object-fit: contain;
}
</style>