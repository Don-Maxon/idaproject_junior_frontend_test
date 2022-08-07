<template>
<preloader v-show="!show"/>
<header  v-show="show"> 
  <h2 @click="scrollToForm">Добавление товара</h2> 
  <sort-select v-model="selector" :options="options"/>
</header>
<div class="container"  v-show="show" ref="container">
  <div class="aside_main_wrapper">
    <aside class="sidebar" >
      <div class="product_form_wrapper">
        <product-form @addProduct="addNewCard" />
      </div>
    </aside>
    <transition-group name="card_list" tag="main">
      <div class="product_wrapper" 
        v-for="card in sortCards" 
        :key="card.id"
        > 
          <product-card  
            
            :img_url="card.img_url" 
            :description="card.description"
            :titel="card.name"
            :price="card.price"
            :id="card.id"
            @dleteCardItem="dleteCard"
          />
      </div>
    </transition-group>
  </div>
</div>
</template>

<script>
import ProductForm from "./components/ProductForm.vue"
import ProductCard from "./components/ProductCard.vue"
import SortSelect from "./components/SortSelect.vue"
import Preloader from "./components/PreLoader.vue"
import _cloneDeep from 'lodash.clonedeep';
import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'App',
  components: {
    ProductForm, 
    ProductCard, 
    Preloader, 
    SortSelect
  },
  data(){
    return{
      cards: [],
      show: false,
      selector: {value: "def", name: "По умолчанию"},
      options: [ 
        {value: "def", name: "По умолчанию"},
        {value: "min", name: "По цене min"},
        {value: "max", name: "По цене max"},
        {value: "name", name: "По наименованию"}
      ]

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
    },

    scrollToForm() {
        this.$refs.container.scrollIntoView({behavior: 'smooth'});
    },
  },
  computed:{
    sortCards(){

      let sortedCards = _cloneDeep(this.cards);
      
      if(this.selector.value === "min"){
        return sortedCards.sort((a, b) => Number(a.price.replace(/\s/g, '')) > Number(b.price.replace(/\s/g, '')) ? 1 : -1)
      } else if(this.selector.value === "max"){
        return sortedCards.sort((a, b) => Number(a.price.replace(/\s/g, '')) < Number(b.price.replace(/\s/g, '')) ? 1 : -1)
      }else if(this.selector.value === "name"){
        return sortedCards.sort((x, y) => x.name.localeCompare(y.name));
      }else if(this.selector.value === "def"){
        return sortedCards
      } else{
        return sortedCards
      }
    }
  },
  mounted(){
    
    if(localStorage.cards){
      this.setCards();
    }
    else{
      localStorage.cards = []
    }  
    
    setTimeout(() => this.show = true, 1500);
  }
}
</script>

<style lang="scss">
@import "normalize.css";
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@600&family=Source+Sans+Pro&display=swap');
@import "@/styles/variables.scss";

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

#app {
  min-height: 100vh;
}

.container{
  max-width: 1440px;
  padding: 0 32px 32px;
  margin: 0 auto;
  align-items: center;
}

header{
  display: flex;
  justify-content: space-between;
  max-width: 1440px;
  padding: 16px 32px;
  margin: 0 auto;
  top: 0;

  h2{
    display: flex;
    box-align:end;
    height: 35px;
    margin: 0;
    font-weight: 600;
    pointer-events: none;
    font-size: 28px;
    line-height: 35px;
  }
}

.aside_main_wrapper{
  display: flex;
  position: relative;
}

aside{
  width: 332px;
  min-height: 100%;
}

main{
  display: flex;
  flex: 1;
  justify-content: flex-start; 
  flex-wrap: wrap;
  max-width: 1044px;
}

.product_form_wrapper{
  position: sticky;
  top: 0;
}

.product_wrapper{
  width: 33.33%;
  padding-left: 16px;

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

@media (max-width: 1280px){
  .product_wrapper{
    width: 50%;
  }
}

@media (max-width: 768px){
  .product_form_wrapper{
    padding-top: 0;
  }

  .container{
    padding: 0 16px 16px;
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
    padding-left: 0px;
    width: 100%;
  }

  header{
    padding-top: 10px;
    padding-bottom: 10px;
    position: sticky;
    z-index: 10;
    background: $bg_color;
  }

  header{
    h2{
      min-height: auto;
      font-size: 1.1em;
      cursor: pointer;
      pointer-events: all;
      height: auto;
    } 
  }
}

</style>
