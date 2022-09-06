<template>
    <div class="form_w24">
        <div class="form">
            <div class="form-item">
                <label for="name-product" class="form__label">Наименование товара<div class="form__label-necess">&bull;
                    </div>
                </label>
                <input type="text" @input="checkError(nameProduct,'nameError')" id="name-product" class="form__input" placeholder="Введите наименование товара"
                    v-model="nameProduct"  :class="{'form__input_error': errors.nameError}">
                <div class="form-item__error" v-if="errors.nameError">Поле является обязательным

                </div>

            </div>


            <div class="form-item">
                <label for="discription-product" class="form__label">Описание товара</label>
                <textarea type="text" id="discription-product" class="form__textarea"
                    placeholder="Введите описание товара" v-model="discriptionProduct"></textarea>
            </div>
            <div class="form-item">
                <label for="link-product" class="form__label">Ссылка на изображение товара<div
                        class="form__label-necess">&bull;</div></label>
                <input type="text" id="link-product" @input="checkError(linkProduct,'linkError')" class="form__input" placeholder="Введите ссылку"
                    v-model="linkProduct"  :class="{'form__input_error': errors.linkError}">
                <div class="form-item__error" v-if="errors.linkError">Поле является обязательным

                </div>
            </div>
            <div class="form-item">
                <label for="price-product" class="form__label">Цена товара<div class="form__label-necess">&bull;</div>
                </label>
                <input type="number" id="price-product" @input="checkError(priceProduct,'priceError')" class="form__input" placeholder="Введите цену"
                    v-model="priceProduct" :class="{'form__input_error': errors.priceError}">
                <div class="form-item__error" v-if="errors.priceError">Поле является обязательным

                </div>
            </div>
            <button class="form__button" @click="addProduct"
                :class="{ 'form__button_disabled': !isActiveButton, 'form__button_active': isActiveButton }">Добавить
                товар</button>
        </div>
    </div>
</template>
<script>
// import { emit } from 'process';
import { ref, reactive, watch } from 'vue'
export default {
    props: {},
    emits: ["addProduct"],
    setup(props, { emit }) {

        const isWatch = ref(true);

        const nameProduct = ref("");
        const discriptionProduct = ref("");
        const linkProduct = ref("");
        const priceProduct = ref("");
        const isActiveButton = ref(false);
        
        watch(() => {

            if (nameProduct.value.length != 0 && linkProduct.value.length != 0 && priceProduct.value.length != 0 && isWatch.value) {
                isActiveButton.value = true;
                isWatch.value = false
            }
            else {
                if (nameProduct.value.length != 0 && linkProduct.value.length != 0 && priceProduct.value.length != 0) {
                    isWatch.value = false
                }
                else {
                    isWatch.value = true;
                    isActiveButton.value = false;
                }

            }
        })

        const errors = ref({
            nameError: false,
            linkError: false,
            priceError: false,
        });
        const addProduct = () => {
           
            const obj = reactive({
                name: null,
                text: null,
                price: null,
                img: null

            })
            if (nameProduct.value?.length != 0) {
                obj.name = nameProduct.value
            } else {
                
                errors.value.nameError = true
            }
            if (discriptionProduct.value?.length != 0) {
                obj.text = discriptionProduct.value
            }
            if (priceProduct.value?.length != 0) {
                const price = priceProduct.value.toString().replace(/\B(?=(\d{3})+(?!\d))/g, " ");
                obj.price = price + " руб."
            }else {
                errors.value.linkError = true
            }
            if (linkProduct.value?.length != 0) {
                
                
                obj.img = linkProduct.value
            }else {
                errors.value.priceError = true
            }
            if (obj.name != null && obj.img != null && obj.price != null) {
                linkProduct.value='';
                nameProduct.value='';
                discriptionProduct.value='';
                priceProduct.value='';

                emit('addProduct', obj);
            }

        }
        const checkError = (name,errorItem) => {
            if(name.length !=0){
                errors.value[errorItem]=false
            }

        }
        return {
            nameProduct,
            discriptionProduct,
            linkProduct,
            priceProduct,
            addProduct,
            isActiveButton,
            isWatch,
            errors,
            checkError,
            
        }
    }

}
</script>
