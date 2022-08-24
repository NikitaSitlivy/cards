<template>

  <div class="card">
    <div class="card__photo" :style="{ backgroundImage: `url('${img}') `}">
      
    </div>
    <!-- <img src="../assets/card.png" class="card__photo"> -->
    <div class="card-container">
      <h2 class="card-container__title">{{title}}</h2>
      <p class="card-container__text">{{text}}</p>
      <span class="card-container__price">{{price}}</span>
    </div>
  </div>

</template>

<script>
 import { ref } from 'vue'

export default {
  props: {
    // title:String,
    // text:String,
    // price:String
    data:Object,
  },
  setup(props) {
    const title = ref(props.data.name);
    const text = ref(props.data.text);
    const price = ref(props.data.price);
    // const img = 'https://html5book.ru/wp-content/uploads/2014/07/html_images.png'
     const img = ref(props.data.img)
    return {
      img,
      title,
      text,
      price
    }
  }

}
</script>

