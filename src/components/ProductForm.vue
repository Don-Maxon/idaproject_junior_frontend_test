<template>
    <form action="" id="add_product_form" onsubmit="return false">
        <div class="normal_item_wrapper">
            <label for="name_product_input" class="required">Наименование товара</label>
            <input 
                type="text" 
                name="name_product_input"
                class="form_item item_height" 
                placeholder="Введите наименование товара"
                v-model="product_item.name"
                :class="{ 'is_invalid': v$.product_item.name.$error }"
            >
            <div v-show="v$.product_item.name.$error" class="is_invalid_massage">Поле является обязательным</div>
        </div>
        <div class="hight_item_wrapper">
            <label for="product_description_textarea" >Описание товара</label>
            <textarea 
                name="product_description_textarea" 
                class="form_item product_description_textarea" 
                placeholder="Введите описание товара"
                v-model="product_item.description"

            ></textarea>
        </div>
        <div class="normal_item_wrapper">
            <label for="url_img_input" class="required">Ссылка на изображение товара</label>
            <input 
                type="text" 
                name="url_img_input" 
                class="form_item item_height"  
                placeholder="Введите ссылку"
                v-model="product_item.img_url"
                :class="{ 'is_invalid': v$.product_item.img_url.$error }"
            >
            <div v-show="v$.product_item.img_url.$error" class="is_invalid_massage">Поле является обязательным</div>  
        </div>
        <div class="normal_item_wrapper">
            <label for="price_input" class="required">Цена товара</label>
            <input 
                type="text" 
                name="price_input" 
                class="form_item item_height" 
                placeholder="Введите цену" 
                :model-modifiers="{ number: true }" 
                v-model.lazy="product_item.price" 
                v-money3="price_config"
                :class="{ 'is_invalid': v$.product_item.price.$error }"
            >
            <div v-show="v$.product_item.price.$error" class="is_invalid_massage">Поле является обязательным</div>
        </div>
        <button  
            class="item_height add_product_btn" 
            :disabled="v$.$error"
            @click="addProduct"
            :class="{ 'disabled_btn': v$.$error, 'active_btn': !v$.$error}"
        >
            Добавить товар
        </button>
    </form>
</template>

<script>
import useVuelidate from '@vuelidate/core'
import { required } from '@vuelidate/validators'

export default {
    name: 'ProductForm',
    setup () {
        return { v$: useVuelidate(),   }
    },
    data(){ 
        return {
            price_config: {
                masked: false,
                thousands: ' ',
                precision: 0, 
                allowBlank: true,   
            },
            product_item:{
                price: null,
                name: "",
                img_url: "",
                description: "",
            },            
        }
    },
    validations () {
        return {
            product_item:{
                price: { required },
                name: { required }, 
                img_url: { required },
            }, 
        }
    },

    methods: {
        addProduct(){
            this.v$.$touch();
            if(!this.v$.$error){
                const product = JSON.parse(JSON.stringify(this.product_item));
                this.$emit("addProduct", product);
                this.v$.$reset();
                this.clearForm();
            }
        },

        clearForm(){
            this.product_item.price = null;
            this.product_item.name = "";
            this.product_item.img_url = "";
            this.product_item.description = "";
        }
    }
}
</script>

<style scoped lang="scss">
@import "@/styles/variables.scss";

#add_product_form{
  padding: 24px;
  box-shadow: $wrap_box_shadow;
  border-radius: 4px;
  background: $bg_color;
  display: flex;
  flex-direction: column;

    label{
        font-size: 10px;
        color: $label_text_color;
        margin-bottom: 4px;
        height: 13px;
    }

    .item_height{
        height: 36px;
    }
}

.form_item{
    box-shadow: 0px 2px 5px $def_shadow_color;
    border-radius: 4px;
    border: 0px;
    outline:none;
    font-size: 12px;
    line-height: 15px;
    text-align: left;
    padding: 10px 16px;
    transition: .3s box-shadow;
}

.form_item:hover{
    box-shadow:0 0 4px $act_shadow_color;
}

.form_item:focus{
    border: 1px solid #95959e;
    box-shadow:0 0 4px $act_shadow_color;
}

.form_item::placeholder{
  font-size: 12px;
  line-height: 15px;
  text-align: left;
  color: $placeholder_text_color;
}

.product_description_textarea{
    resize: none;
    height: 108px;
}

.add_product_btn{
    text-align: center;
    margin-top: 8px;
    border-radius: 10px;
    border: none;
    font-family: 'Inter';
    font-style: normal;
    font-weight: 600;
    font-size: 12px;
    line-height: 15px; 
}

.active_btn{
    background: $act_btn_bg;
    color: $act_btn_color;
    transition:  background-color .3s, .3s box-shadow;
}

.active_btn:hover{
    cursor: pointer;
    background: $act_btn_bg_hover
}

.active_btn:active{
    transition: background-color .3s, box-shadow .3s;
    box-shadow: inset -2px -2px 15px $act_shadow_color;
}

.disabled_btn{
    background: #EEEEEE;
    color: $placeholder_text_color;
    cursor: default;
}

.disabled_btn:hover{
    cursor: default;
}


.required::after {
    width: 4px; 
    height: 4px;
    background: $danger_color;
    border-radius: 50%;
    content: "";
    display: inline-block;
    margin-bottom: 5px;
}

.is_invalid{
    border: 1px solid $danger_color;
}

.is_invalid_massage{
    font-size: 8px;
    line-height: 10px;
    letter-spacing: -0.02em;
    color: $danger_color;
    height: 10px;
    float: left;
    margin: 4px 0 2px 0;
}

.normal_item_wrapper{
    height: 69px;
    display: flex;
    flex-direction: column;
}

.hight_item_wrapper{
    height: 141px;
    display: flex;
    flex-direction: column;
}
</style>