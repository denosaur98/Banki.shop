<template>
  <div class="main">
    <h1 class="title">Картины эпохи Возрождения</h1>
    <div class="blocks_container">
      <div class="block">
        <div class="item1"></div>
        <p class="description">«Рождение Венеры»<br>Сандро Боттичелли</p>
        <div class="price_container">
          <div class="sale">
            <s class="price_sale">2 000 000 $</s>
            <p class="price">1 000 000 $</p>
          </div>
          <button class="btn_main" @click="addToCart($event)">Купить</button>
        </div>
      </div>
      <div class="block">
        <div class="item2"></div>
        <p class="description">«Тайная вечеря»<br>Леонардо да Винчи</p>
        <div class="price_container">
          <p class="nt_sale">3 000 000 $</p>
          <button class="btn_main" @click="addToCart($event)">Купить</button>
        </div>
      </div>
      <div class="block">
        <div class="item3"></div>
        <p class="description">«Сотворение Адама»<br>Микеланджело</p>
        <div class="price_container">
          <div class="sale">
            <s class="price_sale">6 000 000 $</s>
            <p class="price">5 000 000 $</p>
          </div>
          <button class="btn_main" @click="addToCart($event)">Купить</button>
        </div>
      </div>
      <div class="block_sales">
        <div class="item4"></div>
        <p class="description">«Урок анатомии»<br>Рембрандт</p>
        <div class="price_container">
          <p class="price">Продана на аукционе</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    addToCart(event) {
      const btn = event.target
      if (btn.classList.contains('basket')) {
        btn.classList.add('loading')
        btn.innerHTML = '<span class="loading"></span>'
        btn.style.fontSize = '0.6vw'
        setTimeout(() => {
          btn.classList.remove('loading')
          btn.classList.remove('basket')
          btn.innerHTML = 'Купить'
          btn.style.fontSize = '1.02vw'
          btn.disabled = false
        }, 2000)
      } else {
        btn.classList.add('loading')
        btn.innerHTML = '<span class="loading"></span>'
        btn.disabled = true
        setTimeout(() => {
          btn.classList.remove('loading')
          btn.classList.add('basket')
          btn.innerHTML = ''
          btn.style.fontSize = '0.95vw'
          btn.disabled = false
        }, 2000)
      }
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Merriweather&display=swap');
@font-face {
  font-family: 'Merriweather';
}
.main {
  height: 40vw;
}
.title {
  font-family: 'Merriweather';
  font-size: 1.25vw;
  line-height: 1.88vw;
  margin-top: 2.34vw;
  margin-left: 13.33vw;
}
.blocks_container {
  display: flex;
  justify-content: space-between;
  margin-top: 2.03vw;
  margin-left: 13.33vw;
  margin-right: 12.85vw;
}
.block {
  border: 1px solid rgb(187, 187, 187);
  width: 14.58vw;
  height: 17.08vw;
}
.block_sales {
  border: 1px solid rgb(187, 187, 187);
  width: 14.58vw;
  height: 17.08vw;
  opacity: 0.5;
}
.item1 {
  background-image: url('../main/1.png');
  background-size: cover;
  width: 14.58vw;
  height: 8.33vw;
}
.item2 {
  background-image: url('../main/2.png');
  background-size: cover;
  width: 14.58vw;
  height: 8.33vw;
}
.item3 {
  background-image: url('../main/3.png');
  background-size: cover;
  width: 14.58vw;
  height: 8.33vw;
}
.item4 {
  background-image: url('../main/4.png');
  background-size: cover;
  width: 14.58vw;
  height: 8.33vw;
}
.description {
  font-family: 'Merriweather';
  font-style: normal;
  font-weight: 400;
  font-size: 0.94vw;
  line-height: 150%;
  display: flex;
  justify-content: center;
  color: #343030;
}
.price_container {
  display: flex;
  justify-content: center;
}
.price {
  font-family: 'Merriweather';
  font-style: normal;
  font-weight: 700;
  font-size: 0.83vw;
  line-height: 0%;
  align-items: center;
  color: #343030;
  margin-right: 1.30vw;
}
.nt_sale {
  font-family: 'Merriweather';
  font-style: normal;
  font-weight: 700;
  font-size: 0.83vw;
  line-height: 150%;
  align-items: center;
  color: #343030;
  margin-right: 1.30vw;
}
.price_sale {
  opacity: 0.5;
  font-family: 'Merriweather';
  font-style: normal;
  font-weight: 300;
  font-size: 0.73vw;
  line-height: 0%;
}
.btn_main {
  border: 1px solid #403432;
  cursor: pointer;
  color: #FFFFFF;
  font-family: 'Merriweather';
  font-style: normal;
  font-weight: 500;
  font-size: 1.02vw;
  line-height: 150%;
  width: 6.15vw;
  height: 2.65vw;
  background: #403432;
}
.btn_main:not(.loading):not(.basket):hover {
  color: #F4F6F9;
  border: 1px solid #776763;
  background: #776763;
  transition: 0.2s all ease;
}
.loading {
  opacity: 0.5;
}
.basket {
  cursor: pointer;
  border: 1px solid #5B3A32;
  line-height: 150%;
  width: 6.15vw;
  height: 2.65vw;
  background: #5B3A32;
  background-image: url('../main/basket_white.png');
  background-size: 25%;
  background-repeat: no-repeat;
  background-position: center center;
}
.loading::before {
  margin-top: -0.10vw;
  margin-left: -0.16vw;
  content: '';
  width: 20px;
  height: 20px;
  border-radius: 50%;
  border: 2px solid #ccc;
  border-top-color: #333;
  animation: spin 1s linear infinite;
  position: absolute;
  top: calc(50% - 10px);
  left: calc(50% - 10px);
}
@keyframes spin {
  to { transform: rotate(360deg); }
}
.loading {
  position: relative;
  overflow: hidden;
}
.loading span {
  position: relative;
  display: inline-block;
  vertical-align: middle;
  width: 100%;
  text-align: center;
  font-size: 0;
}
</style>