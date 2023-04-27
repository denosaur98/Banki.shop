<template>
  <div class="footer">
    <div class="links_container_footer">
      <a href="#" class="link">Каталог</a>
      <a href="#" class="link">Доставка</a>
      <a href="#" class="link">Оплата</a>
      <a href="#" class="link">Контакты</a>
      <a href="#" class="link">О компании</a>
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

<style>
.footer {
  display: flex;
  justify-content: center;
  height: 5vw;
  width: 100%;
  border-bottom: 1px solid rgb(187, 187, 187);
  background: #E5E5E5;
}
.links_container_footer {
  display: flex;
  margin-top: 1.8vw;
  margin-left: 23.33vw;
}
.link:hover {
  opacity: 0.7;
  transition: 0.3s all ease;
}
.contacts_footer_container {
  display: flex;
  margin-top: 1.35vw;
  margin-left: 7.92vw;
  margin-right: 13.5vw;
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
@media screen and (max-width: 550px) {
  .footer {
    position: fixed;
    width: 100%;
    border-bottom: none;
    height: 8vw;
  }
  .contacts_footer_container {
    display: flex;
    flex-direction: column;
    margin-left: -1vw;
  }
  .contacts {
    font-size: 0.9vw;
    line-height: 100%;
  }
  .links_container_footer {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(2, auto);
    grid-gap: 1.5vw;
    margin-top: 0.5vw;
  }
}
</style>