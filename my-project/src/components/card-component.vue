<template>

  <div class="card">
    <div class="card__photo" :style="{ backgroundImage: `url('${img}') ` }">

    </div>
    <!-- <img src="../assets/card.png" class="card__photo"> -->
    <div class="card-container">
      <h2 class="card-container__title">{{ title }}</h2>
      <p class="card-container__text">{{ text }}</p>
      <span class="card-container__price">{{ price }}</span>
      <div class="card-container__delete" @click="deleteProduct">
        <img src="../assets/trash.svg" alt="trash" class="card-container__trash">
      </div>
    </div>
  </div>

</template>

<script>

import { ref, watchEffect } from 'vue'

export default {
  props: {
    data: Object,
    index: Number,
  },
  emits: ['deleteCard'],
  setup(props, { emit }) {
    const title = ref();
    const text = ref();
    const price = ref();
    const img = ref();
    const indexCard = ref(props.index);
    const deleteProduct = () => {
      emit('deleteCard', indexCard.value);

    };
    watchEffect(() => {
      if (props?.data) {
        title.value = props.data.name
        text.value = props.data.text
        price.value = props.data.price
        img.value = props.data.img
        indexCard.value = props.index
      }

    })
    return {
      img,
      title,
      text,
      price,
      indexCard,
      deleteProduct
    }
  }

}
</script>

