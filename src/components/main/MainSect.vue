<template>
  <div class="main">
    <h1 class="title">Картины эпохи Возрождения</h1>
    <div class="blocks_container">
      <div class="block">
        <div class="item1"></div>
        <p class="description">«Рождение Венеры»<br>Сандро Боттичелли</p>
      </div>
      <div class="block">
        <div class="item2"></div>
        <p class="description">«Тайная вечеря»<br>Леонардо да Винчи</p>
      </div>
      <div class="block">
        <div class="item3"></div>
        <p class="description">«Сотворение Адама»<br>Микеланджело</p>
      </div>
      <div class="block">
        <div class="item4"></div>
        <p class="description">«Урок анатомии»<br>Рембрандт</p>
      </div>
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
  margin-right: 13.33vw;
}
.block {
  border: 1px solid rgb(187, 187, 187);
  width: 14.58vw;
  height: 17.08vw;
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
</style>