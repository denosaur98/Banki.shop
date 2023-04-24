<template>
  <div class="header">
    <div class="links_container">
      <a class="link">Каталог</a>
      <a class="link">Доставка</a>
      <a class="link">Оплата</a>
      <a class="link">Контакты</a>
      <a class="link">О компании</a>
    </div>
    <div class="search_container">
      <input class="search" placeholder="Поиск по названию картины">
      <button class="btn">Найти</button>
    </div>
  </div>
</template>

<script>

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
  margin-right: 18.33vw;
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
</style>