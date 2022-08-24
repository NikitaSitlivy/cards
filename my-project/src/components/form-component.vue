<template>
    <div class="form_w24">
        <div class="form">
            <div class="form-item">
                <label for="name-product" class="form__label">Наименование товара<div class="form__label-necess">&bull;
                    </div>
                </label>
                <input type="text" id="name-product" class="form__input" placeholder="Введите наименование товара"
                    v-model="nameProduct">
            </div>

            <div class="form-item">
                <label for="discription-product" class="form__label">Описание товара</label>
                <textarea type="text" id="discription-product" class="form__textarea"
                    placeholder="Введите описание товара" v-model="discriptionProduct"></textarea>
            </div>
            <div class="form-item">
                <label for="link-product" class="form__label">Ссылка на изображение товара<div
                        class="form__label-necess">&bull;</div></label>
                <input type="text" id="link-product" class="form__input" placeholder="Введите ссылку" v-model="linkProduct">
            </div>
            <div class="form-item">
                <label for="price-product" class="form__label">Цена товара<div class="form__label-necess">&bull;</div>
                </label>
                <input type="text" id="price-product" class="form__input" placeholder="Введите цену" v-model="priceProduct">
            </div>
            <button class="form__button" @click="addProduct">Добавить товар</button>
        </div>
    </div>
</template>
<script>
// import { emit } from 'process';
import { ref,  reactive } from 'vue'
export default {
    props:{},
    emits:["addProduct"],
    setup(props, {emit}) {
        const nameProduct = ref("");
        const discriptionProduct = ref("");
        const linkProduct = ref("");
        const priceProduct = ref("");
        const addProduct = () =>{
            const obj = reactive({
                name: null,
                text: null,
                price: null,
                img: null

            })
            if (nameProduct.value.lenght !=0) {
                obj.name = nameProduct.value
            }
            if (discriptionProduct.value.lenght !=0) {
                obj.text = discriptionProduct.value
            }
            if (priceProduct.value.lenght !=0) {
                obj.price = priceProduct.value
            }
            if (linkProduct.value.lenght !=0) {
                obj.img = linkProduct.value
            }
            
            emit('addProduct',obj);
        }
        return {
            nameProduct,
            discriptionProduct,
            linkProduct,
            priceProduct,
            addProduct
        }
    }

}
</script>
