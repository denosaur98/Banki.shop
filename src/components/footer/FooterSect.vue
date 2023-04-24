<template>
  <div class="footer">
    <div class="links_container">
      <a class="link">Каталог</a>
      <a class="link">Доставка</a>
      <a class="link">Оплата</a>
      <a class="link">Контакты</a>
      <a class="link">О компании</a>
    </div>
    <div class="contacts_footer_container">
      <div class="contacts_container">
        <div class="phone"></div>
        <p class="contacts">+7 (812) 555-55-55</p>
      </div>
      <div class="contacts_container">
        <div class="geo"></div>
        <p class="contacts">г. Санкт-Петербург, ул. Ефимова, 3</p>
      </div>   
    </div>
  </div>
</template>

<script>

</script>

<style>
.footer {
  display: flex;
  justify-content: center;
  height: 5vw;
  border-bottom: 1px solid rgb(187, 187, 187);
  background: #E5E5E5;
}
.contacts_footer_container {
  display: flex;
  margin-top: 1.15vw;
  margin-left: 7.92vw;
  margin-right: 15.33vw;
}
.contacts {
  font-family: 'Merriweather';
  font-style: normal;
  font-weight: 400;
  font-size: 0.73vw;
  line-height: 150%;
  align-items: center;
  color: #555555;
  white-space: nowrap;
}
.contacts_container {
  display: flex;
  margin-right: 2.81vw;
}
.phone {
  background-image: url('../footer/phone.png');
  background-size: cover;
  width: 0.73vw;
  height: 0.73vw;
  margin-right: 0.47vw;
  margin-top: 0.85vw;
}
.geo {
  background-image: url('../footer/geo.png');
  background-size: cover;
  width: 0.53vw;
  height: 0.73vw;
  margin-right: 0.47vw;
  margin-top: 0.85vw;
}
</style>