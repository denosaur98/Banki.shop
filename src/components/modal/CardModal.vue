<template>
  <div class="modal" v-if="showModal">
    <div class="modal-overlay" @click="closeModal"></div>
    <div class="modal-container">
      <div class="modal-header">
        <h3 class="title_picture">{{ card.title }}</h3>
        <button class="close-button" @click="closeModal">&times;</button>
      </div>
      <p class="author">{{ card.author }}</p>
      <div class="modal-content">
        <div class="modal-slider">
          <div class="slider-button slider-button-left" @click="prevImage">
            &#9668;<i class="fas fa-chevron-left"></i>
          </div>
          <img :src="currentImage" :key="currentImage" class="slider img"/>
          <div class="slider-button slider-button-right" @click="nextImage">
            &#9658;<i class="fas fa-chevron-right"></i>
          </div>
        </div>
        <p class="description_modal">{{ card.description }}</p>
        <p class="price_modal">Цена: <em>{{ card.price }} $</em></p>
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
    }
  },
  computed: {
    currentImage() {
      return this.card.images[this.currentImageIndex]
    }
  },
  methods: {
    closeModal() {
      this.$emit("close-modal")
    },
    prevImage() {
      if (this.currentImageIndex === 0) {
        this.currentImageIndex = this.card.images.length - 1
      } else {
        this.currentImageIndex--
      }
    },
    nextImage() {
      if (this.currentImageIndex === this.card.images.length - 1) {
        this.currentImageIndex = 0
      } else {
        this.currentImageIndex++
      }
    },
  }
}
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
  background: rgb(218, 218, 218);
}
.modal-header {
  margin-top: -2.5vw;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.close-button {
  font-size: 3.2vw;
  background-color: transparent;
  border: none;
  cursor: pointer;
  color: #343030;
}
.title_picture {
  display: flex;
  font-size: 2.2vw;
  color: #343030;
  font-style: normal;
  font-weight: bold;
  font-family: 'Merriweather';
}
.author {
  margin-left: 1.5vw;
  color: #343030;
  font-weight: 500;
  font-size: 1.02vw;
  font-family: 'Merriweather';
  margin-top: -2vw;
  font-style: italic;
}
.description_modal {
  margin-top: 1.9vw;
  color: #343030;
  font-style: normal;
  font-weight: 500;
  font-size: 1.05vw;
  font-family: 'Merriweather';
}
.price_modal {
  color: #343030;
  font-style: normal;
  font-weight: bolder;
  font-size: 2vw;
  font-family: 'Merriweather';
  text-decoration: underline;
}
.modal-content {
  margin-top: 20px;
}
.slider-button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: rgba(0, 0, 0, 0.4);
  border: none;
  cursor: pointer;
  color: #fff;
  width: 40px;
  height: 80px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 30px;
  font-weight: bold;
  transition: background-color 0.2s ease-in-out;
  z-index: 999;
}
.slider-button-left {
  left: 0;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
}
.slider-button-right {
  right: 0;
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
}
.slider-button:hover {
  background-color: rgba(0, 0, 0, 0.7);
}
.slider {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
  width: 43.92vw;
  height: 29.28vw;
  background-size: cover;
}
.img {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  width: 43.92vw;
  height: 29.28vw;
  background-size: cover;
}
.modal-container::-webkit-scrollbar {
  width: 5px;
  background-color: #343030;
}
.modal-container::-webkit-scrollbar-track {
  background-color: #343030;
}
.modal-container::-webkit-scrollbar-thumb {
  background-color: #888;
  border-radius: 5px;
}
</style>