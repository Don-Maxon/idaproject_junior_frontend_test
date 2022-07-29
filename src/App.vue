<template>
<div class="container">
  <div class="top_bar"> 
  <h1>Добавление товара</h1> 
    <select name="sort_select" id="sort_select">
      <option>По цене min</option>
      <option>По цене max</option>
      <option>По наименованию</option>
    </select>
  </div>
  <div class="aside_main_wrapper">
    <aside class="sidebar">
      <form action="" class="add_product_form">
        <label for="">Наименование товара</label>
        <input type="text" id="name_product_input" placeholder="Введите наименование товара">
      </form>
    </aside>
    <main class="main">
      <div>main</div>
    </main>
  </div>

</div>

  


  

</template>

<script>


export default {
  name: 'App',
  components: {}
}
</script>

<style lang="scss">
@import "normalize.css";
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap');

$text-color: #3F3F3F;
$body-bg-color: #E5E5E5;
$label-text-color: #49485E;
$placeholder-text-color:  #B4B4B4;
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
  // background-color: #af9e9e;
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

.add_product_form{
  padding: 24px;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  background: #FFFEFB;
  display: flex;
  flex-direction: column;
}

.add_product_form label{
  font-size: 10px;
  color: $label-text-color;
  margin-bottom: 4px;
  
}

#add_product_form::placeholder{
  font-size: 12px;
  line-height: 15px;
  text-align: left;
  color: $placeholder-text-color;
}

#name_product_input{
box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
border-radius: 4px;
border: none;
display: block;
font-size: 12px;
line-height: 15px;
text-align: left;
padding: 10px 16px;
}





main{
  max-width: 1044px;
  // background: green;
   flex: 1;
}


</style>
