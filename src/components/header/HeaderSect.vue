<template>
  <div class="header">
    <div class="links_container">
      <a href="#" class="link">Каталог</a>
      <a href="#" class="link">Доставка</a>
      <a href="#" class="link">Оплата</a>
      <a href="#" class="link">Контакты</a>
      <a href="#" class="link">О компании</a>
    </div>
    <div class="search_container">
      <input class="search" placeholder="Поиск по названию картины" v-model="search" @input="searchPaintings">
      <button class="btn" @click="searchPaintings" title="Обновить">Найти</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      allPaintings: [
        {id: 1, name: "Рождение Венеры", author: "Сандро Боттичелли", price: 1000000, sale: 2000000},
        {id: 2, name: "Тайная вечеря", author: "Леонардо да Винчи", price: 3000000},
        {id: 3, name: "Сотворение Адама", author: "Микеланджело", price: 5000000, sale: 6000000},
        {id: 4, name: "Урок анатомии", author: "Рембрандт", price: null, sold: true}
      ],
      paintings: [],
      search: '',
    }
  },
  created() {
    this.paintings = this.allPaintings
  },
  methods: {
    searchPaintings() {
      let filteredPaintings = this.allPaintings.filter(painting => painting.name.toLowerCase().includes(this.search.toLowerCase()))
      this.paintings = filteredPaintings.length > 0 ? filteredPaintings : null
      let blocks = document.querySelectorAll('.block, .block_sales')
      blocks.forEach(block => {
        let paintingName = block.querySelector('.description').textContent.toLowerCase()
        if (!paintingName.includes(this.search.toLowerCase())) {
          block.style.display = 'none'
        } else {
          block.style.display = 'block'
        }
      })
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Merriweather&display=swap');
@font-face {
  font-family: 'Merriweather';
}
.header {
  display: flex;
  justify-content: center;
  height: 5vw;
  border-bottom: 1px solid rgb(187, 187, 187);
}
.links_container {
  display: flex;
  margin-top: 1.8vw;
  margin-left: 23.33vw;
}
.search_container {
  display: flex;
  margin-top: 1.15vw;
  margin-left: 7.92vw;
  margin-right: 19.33vw;
}
.link {
  cursor: pointer;
  font-family: 'Merriweather';
  font-style: normal;
  font-weight: 400;
  font-size: 1.02vw;
  line-height: 150%;
  text-decoration: none;
  color: #343030;
  margin-right: 2.50vw;
  white-space: nowrap;
}
.search {
  background: #E5E5E5;
  padding-left: 16px;
  border: 1px solid rgb(187, 187, 187);
  outline: none;
  font-family: 'Merriweather';
  font-style: normal;
  font-weight: 400;
  font-size: 0.73vw;
  line-height: 150%;
  width: 15.31vw;
  height: 2.4vw;
}
.btn {
  border: 1px solid #403432;
  cursor: pointer;
  color: #FFFFFF;
  font-family: 'Merriweather';
  font-style: normal;
  font-weight: 500;
  font-size: 1.02vw;
  line-height: 150%;
  width: 6.35vw;
  height: 2.65vw;
  background: #403432;
}
.btn:hover {
  color: #F4F6F9;
  border: 1px solid #776763;
  background: #776763;
  transition: 0.2s all ease;
}
</style>