<template>
  <form action="" id="add_product_form">
    <label for="name_product_input" class="required">Наименование товара</label>
    <input type="text" id="name_product_input" class="form_item item_height" placeholder="Введите наименование товара">
    <label for="product_description_textarea" >Описание товара</label>
    <textarea name="product_description_textarea" id="product_description_textarea" class="form_item" placeholder="Введите описание товара"></textarea>
    <label for="url_img_input" class="required">Ссылка на изображение товара</label>
    <input type="url" id="url_img_input" class="form_item item_height"  placeholder="Введите ссылку">
    <label for="price_input" class="required">Ссылка на изображение товара</label>
    <input type="text" id="price_input" class="form_item item_height" placeholder="Введите цену">
    <button id="add_product_btn" class="item_height"> Добавить товар</button>
</form>
</template>

<script>
export default {
    name: 'ProductForm',
}
</script>

<style lang="scss">
$label-text-color: #49485E;
$placeholder-text-color:  #B4B4B4;

#add_product_form{
  padding: 24px;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  background: #FFFEFB;
  display: flex;
  flex-direction: column;
}

#add_product_form label{
  font-size: 10px;
  color: $label-text-color;
  margin-bottom: 4px;
  height: 13px;
}

#add_product_form .form_item{
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
    border: none;
    font-size: 12px;
    line-height: 15px;
    text-align: left;
    padding: 10px 16px;
    margin-bottom: 16px;
}

#add_product_form .item_height{
    height: 36px;
}

.form_item::placeholder{
  font-size: 12px;
  line-height: 15px;
  text-align: left;
  color: $placeholder-text-color;
}


#product_description_textarea{
    resize: none;
    height: 108px;
}

#add_product_btn{
    text-align: center;
    margin-top: 8px;
    background: #EEEEEE;
    border-radius: 10px;
    border: none;
    font-family: 'Inter';
    font-style: normal;
    font-weight: 600;
    font-size: 12px;
    line-height: 15px;
    color: $placeholder-text-color;
}

.required::after {
width: 4px; 
height: 4px;
background: #FF8484;
border-radius: 50%;
content: "";
display: inline-block;
margin-bottom: 5px;
}

</style>