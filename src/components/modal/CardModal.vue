<template>
  <div class="modal" v-if="showModal">
    <div class="modal_overlay" @click="closeModal"></div>
    <div class="modal_container">
      <div class="modal_header">
        <h3 class="title_picture">{{ card.title }}</h3>
        <button class="close_button" @click="closeModal">&times;</button>
      </div>
      <p class="author">{{ card.author }}</p>
      <div class="modal_content">
        <div class="modal_slider">
          <div class="slider_button slider_button_left" @click="prevImage">
            &#9668;<i class="fas fa-chevron-left"></i>
          </div>
          <img :src="currentImage" :key="currentImage" class="slider img"/>
          <div class="slider_button slider_button_right" @click="nextImage">
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
.modal_overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
}
.modal_container {
  position: relative;
  margin: auto;
  max-width: 43.92vw;
  max-height: 90%;
  overflow: auto;
  background-color: #fff;
  border-radius: 5px;
  padding: 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  background: rgb(218, 218, 218);
}
.modal_header {
  margin-top: -2.5vw;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.close_button {
  font-size: 3.2vw;
  background-color: transparent;
  border: none;
  cursor: pointer;
  color: #343030;
}
.close_button:hover {
  opacity: 0.7;
  transition: 0.3s all ease;
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
.modal_content {
  margin-top: 20px;
}
.slider_button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: rgba(0, 0, 0, 0.4);
  border: none;
  cursor: pointer;
  color: #fff;
  width: 2.93vw;
  height: 5.86vw;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 2.2vw;
  font-weight: bold;
  transition: background-color 0.2s ease-in-out;
  z-index: 999;
}
.slider_button_left {
  left: 0;
  border-top-right-radius: 0.37vw;
  border-bottom-right-radius: 0.37vw;
}
.slider_button_right {
  right: 0;
  border-top-left-radius: 0.37vw;
  border-bottom-left-radius: 0.37vw;
}
.slider_button:hover {
  background-color: rgba(0, 0, 0, 0.7);
}
.slider {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 1.46vw;
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
.modal_container::-webkit-scrollbar {
  width: 5px;
  background-color: #343030;
}
.modal_container::-webkit-scrollbar-track {
  background-color: #343030;
}
.modal_container::-webkit-scrollbar-thumb {
  background-color: #888;
  border-radius: 5px;
}
@media screen and (max-width: 550px) {
  .block {
    width: 40vw;
    height: 50vw;
  }
  .modal {
    margin-top: 25vw;
  }
  .modal_container {
    min-width: 50vw;
    height: 40%;
  }
  .title_picture {
    font-size: 3vw;
  }
  .author {
    font-size: 2vw;
  }
  .img {
    min-width: 50vw;
    height: 30vw;
  }
  .description_modal {
    font-size: 1.7vw;
  }
  .price_modal {
    font-size: 2.5vw;
  }
}
</style>