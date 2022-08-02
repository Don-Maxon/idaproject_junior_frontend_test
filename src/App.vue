<template>
  <preloader v-show="!show"/>

<div class="container" v-show="show">
  
  <div class="top_bar"> 
  <h2>Добавление товара</h2> 
    <sort-select v-model="selector"/>
  </div>
  <div class="aside_main_wrapper">
    <aside class="sidebar">
      <div class="product_form_wrapper">
        <product-form @addProduct="addNewCard"/>
      </div>
    </aside>
    <transition-group name="card_list" tag="main">
      <product-card  
        v-for="card in sortCards" 
        :key="card.id"
        :img_url="card.img_url" 
        :description="card.description"
        :titel="card.name"
        :price="card.price"
        :id="card.id"
        @dleteCardItem="dleteCard"
      />
    </transition-group>
  </div>
</div>

</template>

<script>
import ProductForm from "./components/ProductForm.vue"
import ProductCard from "./components/ProductCard.vue"
import SortSelect from "./components/SortSelect.vue"
import Preloader from "./components/PreLoader.vue"
import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'App',
  components: {ProductForm, ProductCard, SortSelect, Preloader},
  data(){
    return{
      cards: [],
      selector: "def",
      show: true,
    }
  },
  methods:{
    addNewCard(item){
      item.id = uuidv4();
      this.cards.push(item)
      this.setLocalStorageCards(this.cards)
    },

    dleteCard(id){
      this.cards = this.cards.filter(item => item.id != id);
      this.setLocalStorageCards(this.cards)
    },

    setLocalStorageCards(cards){
      localStorage.setItem('cards', JSON.stringify(cards));
    },

    setCards(){
      this.cards = JSON.parse(localStorage.getItem('cards'));
    }
  },
  computed:{
    sortCards(){

      let sortedCards = JSON.parse(JSON.stringify(this.cards))
      
      if(this.selector === "min"){
        return sortedCards.sort((a, b) => Number(a.price.replace(/\s/g, '')) > Number(b.price.replace(/\s/g, '')) ? 1 : -1)
      } else if(this.selector === "max"){
        return sortedCards.sort((a, b) => Number(a.price.replace(/\s/g, '')) < Number(b.price.replace(/\s/g, '')) ? 1 : -1)
      }else if(this.selector === "name"){
        return sortedCards.sort((x, y) => x.name.localeCompare(y.name));
      }else if(this.selector === "def"){
        return sortedCards
      } else{
        return sortedCards
      }
    }
  },
  mounted: async function(){
    
    if(localStorage.cards){
      console.log(1);
      this.setCards();
    }
    else{
      localStorage.cards = []
    }  
  }
}
</script>

<style lang="scss">
@import "normalize.css";
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@600&family=Source+Sans+Pro&display=swap');

$text_color: #3F3F3F;
$body_bg_color: rgba(255, 254, 251, 0.8);

* {
  box-sizing: border-box;
}

body{
  background: $body_bg_color;
  font-family: 'Source Sans Pro';
  font-weight: 400;
	font-size: 16px;
	color: $text-color;
}

h2{
  height: 35px;
  margin: 0;
  font-weight: 600;
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
  margin: 0;
}

.aside_main_wrapper{
  display: flex;
  position: relative;
}

aside{
  width: 332px;
  min-height: 100%;
}

.product_form_wrapper{
  padding-top: 24px;
  position: sticky;
  top: 0;
}

main{
  display: flex;
  flex: 1;
  justify-content: flex-start; 
  flex-wrap: wrap;
  padding-top: 24px;
  max-width: 1044px;
}

.product_wrapper{
  margin-left: 16px;
  margin-bottom: 16px;

}

.product_wrapper:last-of-type{
  margin-right: auto;
}

.card_list-move,
.card_list-enter-active,
.card_list-leave-active {
  transition: all 0.5s ease;
}

.card_list-enter-from,
.card_list-leave-to {
  opacity: 0;
  transform: scale(0.5);
}

@media (max-width: 768px){

  .container{
    padding: 32px 16px;
  }

  .aside_main_wrapper{
    flex-direction: column;
    justify-content: center;
  }

  aside{
    width: 100%;
    margin-bottom: 16px;
  }
  main{
    justify-content: space-between;
  }
  .product_wrapper{
    margin-left: 0px;
    width: 100%;
  }

  .top_bar h2{
    height: auto;
    font-size: 1.5em;
  }
}

</style>
