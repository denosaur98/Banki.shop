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
          <button class="btn_main" @click="addToCart($event)" data-id="product-1">Купить</button>
        </div>
        <div>
          <button class="btn_modal" @click="showModalOne = true"></button>
          <CardModal :card="selectedCardOne" :show-modal="showModalOne" @close-modal="showModalOne = false"/>
        </div>
      </div>
      <div class="block">
        <div class="item2"></div>
        <p class="description">«Тайная вечеря»<br>Леонардо да Винчи</p>
        <div class="price_container">
          <p class="nt_sale">3 000 000 $</p>
          <button class="btn_main" @click="addToCart($event)" data-id="product-2">Купить</button>
        </div>
        <div>
          <button class="btn_modal" @click="showModalTwo = true"></button>
          <CardModal :card="selectedCardTwo" :show-modal="showModalTwo" @close-modal="showModalTwo = false"/>
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
          <button class="btn_main" @click="addToCart($event)" data-id="product-3">Купить</button>
        </div>
        <div>
          <button class="btn_modal" @click="showModalThree = true"></button>
          <CardModal :card="selectedCardThree" :show-modal="showModalThree" @close-modal="showModalThree = false"/>
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
import CardModal from '../modal/CardModal.vue'
// import one from '../main/modalOne/one.jpg';
// import two from '../main/modalOne/two.jpg';
// import three from '../main/modalOne/three.jpg';
// import four from '../main/modalTwo/four.jpg';
// import five from '../main/modalTwo/five.jpg';
// import six from '../main/modalTwo/six.jpg';
// import seven from '../main/modalThree/seven.jpg';
// import eight from '../main/modalThree/eight.jpg';
// import nine from '../main/modalThree/nine.jpg';
export default {
  components: {
    CardModal
  },
  data() {
    return {
      showModalOne: false,
      selectedCardOne: {
        title: "«Рождение Венеры»",
        author: "Сандро Боттичелли",
        images: [
          'https://i2.wp.com/arts-dnevnik.ru/wp-content/uploads/2017/07/IMG_4400.jpg',
          'https://artfactor.com.ua/image/catalog/gallery/002651/preview/mod_id/1/002651_1_1.jpg',
          'https://cdn.leroymerlin.ru/lmru/image/upload/v1635381094/b_white,c_pad,d_photoiscoming.png,f_auto,h_600,q_auto,w_600/lmcode/7QxyBZby90i1wbNUeaGYXQ/93702933_02.jpg'
        ],
        description: "Картина итальянского художника тосканской школы Сандро Боттичелли. Представляет собой живопись темперой на холсте размером 172,5 × 278,5 см. В настоящее время хранится в галерее Уффици, Флоренция.",
        price: '1 000 000',
      },
      showModalTwo: false,
      selectedCardTwo: {
        title: "«Тайная вечеря»",
        author: "Леонардо да Винчи",
        images: [
          'https://avatars.dzeninfra.ru/get-zen_doc/1779163/pub_5dfa9d973642b607cd29c9ac_5dfa9e1ed7859b00b2dd19e4/scale_1200',
          'https://artfactor.com.ua/image/catalog/gallery/001001/preview/mod_id/1/001001_1_1.jpg',
          'https://walldeco.ua/img/gallery_merged/122/00256.jpg',
        ],
        description: "Монументальная роспись работы Леонардо да Винчи, изображающая сцену последней трапезы Христа со своими учениками. Создана в 1495—1498 годы в доминиканском монастыре Санта-Мария-делле-Грацие в Милане.",
        price: '3 000 000',
      },
      showModalThree: false,
      selectedCardThree: {
        title: "«Сотворение Адама»",
        author: "Микеланджело",
        images: [
          'https://cs9.pikabu.ru/post_img/big/2016/09/17/0/1474059896122877083.jpg',
          'https://artposter.com.ua/image/catalog/gallery/product_images/000157/product_type/picture/000157_1_1_picture.jpg',
          'https://cs1.livemaster.ru/storage/db/c0/aa0a12ce907fbbfc4d0424fb2au1--kartiny-i-panno-sotvorenie-adama.jpg'
        ],
        description: "Фреска Микеланджело, написанная около 1511 года. Фреска является четвёртой из девяти центральных композиций потолка Сикстинской капеллы, посвящённых девяти сюжетам книги Бытия. ",
        price: '5 000 000',
      }
    }
  },
  methods: {
    addToCart(event) {
      const btn = event.target
      const productId = btn.getAttribute('data-id')
      const state = localStorage.getItem(productId) || 'btn_main'
      if (state === 'basket') {
        btn.classList.add('loading')
        btn.innerHTML = '<span class="loading"></span>'
        btn.style.fontSize = '0.6vw'
        setTimeout(() => {
          btn.classList.remove('loading')
          btn.classList.remove('basket')
          btn.innerHTML = 'Купить'
          btn.style.fontSize = '1.02vw'
          btn.disabled = false
          localStorage.setItem(productId, 'btn_main')
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
          localStorage.setItem(productId, 'basket')
        }, 2000)
      }
    },
    initState() {
      const btns = document.querySelectorAll('.btn_main')
      btns.forEach(btn => {
        const productId = btn.getAttribute('data-id')
        const state = localStorage.getItem(productId)
        if (state === 'basket') {
          btn.classList.add('basket')
          btn.innerHTML = ''
          btn.style.fontSize = '0.95vw'
        } else {
          btn.classList.remove('basket')
          btn.innerHTML = 'Купить'
          btn.style.fontSize = '1.02vw'
        }
      })
    },
    setImagesSize() {
      this.selectedCardOne.images.forEach(img => {
        img.style.width = "500px"
        img.style.height = "400px"
      })
      this.selectedCardTwo.images.forEach(img => {
        img.style.width = "500px"
        img.style.height = "400px"
      })
      this.selectedCardThree.images.forEach(img => {
        img.style.width = "500px"
        img.style.height = "400px"
      })
    }
  },
  mounted() {
    this.initState()
    this.setImagesSize()
  },
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
  position: relative;
  font-family: 'Merriweather';
  font-style: normal;
  font-weight: 400;
  font-size: 0.94vw;
  line-height: 150%;
  display: flex;
  justify-content: center;
  color: #343030;
  z-index: -1;
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
  transition: 0.3s all ease;
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
.basket:hover {
  transition: 0.3s all ease;
  box-shadow: 1px 1px 10px 1px #5B3A32;
}
.loading::before {
  margin-top: -0.10vw;
  margin-left: -0.16vw;
  content: '';
  width: 1.46vw;
  height: 1.46vw;
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
.btn_modal {
  position: relative;
  cursor: pointer;
  display: flex;
  width: 14.58vw;
  height: 12vw;
  margin-top: -16vw;
  background: none;
  border: none;
  z-index: 1;
}
@media screen and (max-width: 550px) {
  .main {
    height: 100%;
  }
  .title {
    display: flex;
    margin-left: 34.5vw;
    margin-top: 9vw;
    font-size: 2vw;
  }
  .blocks_container {
    display: grid;
    margin-top: 5vw;
    grid-gap: 2vw;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(2, auto);
    justify-items: center;
    width: 37.38vw;
    margin-left: 8.5vw;
    margin-bottom: 5vw;
  }
  .block {
    width: 40vw;
    height: 50vw;
  }
  .block_sales {
    width: 40vw;
    height: 50vw;
  }
  .item1, .item2, .item3, .item4 {
    width: 40vw;
    height: 22.67vw;
  }
  .description {
    font-size: 3vw;
  }
  .btn_main {
    margin-top: 0.7vw;
    cursor: pointer;
    font-size: 4.02vw;
    line-height: 150%;
    width: 8.15vw;
    height: 4.65vw;
  }
  .price {
    font-size: 2.5vw;
  }
  .price_sale {
    display: flex;
    line-height: 110%;
    margin-top: 0.6vw;
    font-size: 2vw;
  }
  .nt_sale {
    margin-top: 1vw;
    font-size: 2.5vw;
  }
  .loading::before {
    margin-top: 1.5vw;
    margin-left: 1.5vw;
    content: '';
    width: 1.2vw;
    height: 1.2vw;
  }
  .btn_modal {
    display: flex;
    margin-top: -45.5vw;
    width: 40vw;
    height: 35vw;
  }
}
</style>