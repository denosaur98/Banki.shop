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
          <div class="slider-button slider-button-left" @click="prevImage">
            A<i class="fas fa-chevron-left"></i>
          </div>
          <img :src="currentImage" :key="currentImage" class="slider img"/>
          <div class="slider-button slider-button-right" @click="nextImage">
            Aaaaa<i class="fas fa-chevron-right"></i>
          </div>
        </div>
        <p>{{ card.description }}</p>
        <p>Цена: {{ card.price }}</p>
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
  data() {
    return {
      currentImageIndex: 0
    };
  },
  computed: {
    currentImage() {
      return this.card.images[this.currentImageIndex];
    }
  },
  methods: {
    closeModal() {
      this.$emit("close-modal");
    },
    prevImage() {
      if (this.currentImageIndex > 0) {
        this.currentImageIndex--;
      }
    },
    nextImage() {
      if (this.currentImageIndex < this.card.images.length - 1) {
        this.currentImageIndex++;
      }
    },
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
.slider-button {
  z-index: 999;
  position: absolute;
  display: flex;
  justify-content: space-between;
  top: 50%;
  transform: translateY(-50%);
  background-color: transparent;
  border: none;
  cursor: pointer;
  color: #fff;
}
.slider-button-left {
  border: 1px solid black;
}
.slider-button-right {
  display: flex;
  float: right;
  border: 1px solid black;
  margin-left: 200px;
}
.slider {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
  max-width: 600px;
  max-height: 400px;
  background-size: cover;
}
.img {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  width: 600px;
  height: 400px;
  background-size: cover;
}
</style>