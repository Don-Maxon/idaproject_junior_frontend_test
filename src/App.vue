<template>
<div class="container">
  <div class="top_bar"> 
  <h1>Добавление товара</h1> 
    <sort-select/>
  </div>
  <div class="aside_main_wrapper">
    <aside class="sidebar">
      <product-form/>
    </aside>
    <main>
      <div class="product_wrapper" v-for="i in 5" :key="i">
        <product-card  
        :img_url="'http://1001goroskop.ru/img/gadanie/derevo_zh/_derevo.jpg'" 
        :description="'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк'"
        :titel="'титул'"
        :price="'150'"
        />
      </div>
    </main>
  </div>
</div>

</template>

<script>
import ProductForm from "./components/ProductForm.vue"
import ProductCard from "./components/ProductCard.vue"
import SortSelect from "./components/SortSelect.vue"

export default {
  name: 'App',
  components: {ProductForm, ProductCard, SortSelect}
}
</script>

<style lang="scss">
@import "normalize.css";
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@600&family=Source+Sans+Pro&display=swap');

$text-color: #3F3F3F;
$body-bg-color: #E5E5E5;


* {
  box-sizing: border-box;
}

body{
  background: rgba(255, 254, 251, 0.8);
  font-family: 'Source Sans Pro';
  font-weight: 400;
	font-size: 16px;
	color: $text-color;
}

h1{
  height: 35px;
  font-weight: 600;
  margin: 0;
  
}

#app {
  min-height: 100vh;
}

.container{
  max-width: 1440px;
  padding: 32px 32px;
  margin: 0 auto;
  align-items: center;
}

.top_bar{
  display: flex;
  justify-content: space-between;
  margin: 0 0 16px 0 ;
}

.aside_main_wrapper{
  display: flex;
}

aside{
  width: 332px;
  width: 332px;
}

main{
  max-width: 1044px;

  flex: 1;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  padding-left: auto;
  
}

.product_wrapper{
  margin-left: 16px;
  margin-bottom: 16px;

}

.product_wrapper:last-of-type{
  margin-right: auto;
}




</style>
