<template>
  <h1 class="title-main">Добавление товара</h1>
  <div class="page-flex">
    <formComponent @addProduct='getProduct' />
    <div class="card-wrap">
      <template v-for="(item, index) in cardData" :key="index">
        <cardComponent :data="item" :index='index' @deleteCard='deleteCard' />
      </template>
    </div>
  </div>
</template>

<script>

import cardComponent from './components/card-component.vue'
import formComponent from './components/form-component.vue';

import { ref } from 'vue'

export default {

  components: {
    cardComponent,
    formComponent

  },
  setup() {

    const cardData = ref([
      {
        name: 'Наименование товара1',
        text: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        price: '10 000 руб.',
        img: 'https://static.onlinetrade.ru/img/actions/vstrechaem_osen_v_bossa_nova__1661957298.jpg'

      },
      {
        name: 'Наименование товара2',
        text: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        price: '10 000 руб.',
        img: 'https://static.onlinetrade.ru/img/actions/vstrechaem_osen_v_bossa_nova__1661957298.jpg'

      },
      {
        name: 'Наименование товара3',
        text: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        price: '10 000 руб.',
        img: 'https://static.onlinetrade.ru/img/actions/vstrechaem_osen_v_bossa_nova__1661957298.jpg'

      },
      {
        name: 'Наименование товара4',
        text: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        price: '10 000 руб.',
        img: 'https://static.onlinetrade.ru/img/actions/vstrechaem_osen_v_bossa_nova__1661957298.jpg'

      },
      {
        name: 'Наименование товара5',
        text: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        price: '10 000 руб.',
        img: 'https://static.onlinetrade.ru/img/actions/vstrechaem_osen_v_bossa_nova__1661957298.jpg'

      },
      {
        name: 'Наименование товар6',
        text: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        price: '10 000 руб.',
        img: 'https://static.onlinetrade.ru/img/actions/vstrechaem_osen_v_bossa_nova__1661957298.jpg'

      },
    ]);
    const getProduct = (e) => {
      cardData.value.push(e)
    }
    const deleteCard = (index) => {
      cardData.value.splice(index, 1)
    }
    return {
      cardData,
      getProduct,
      deleteCard

    }
  }
}
</script>

<style>
#app {
  font-family: 'Source Sans Pro', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 32px;

}
</style>
