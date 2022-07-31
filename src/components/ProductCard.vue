<template>
        <div class="card_wrapper">
                <div class="img_wrapper"> 
                        <img src="../assets/pages/default_card_picture.png" alt="">
                </div>
                <div class="text_wrapper"> 
                        <h3>Наименование товара</h3>
                        <div class="description">
                                Довольно-таки интересное описание товара в несколько строк. 
                                Довольно-таки интересное описание товара в несколько строк
                        </div>
                        <div class="price">10 000 руб.</div>
                </div>
        </div>
</template>

<script>
export default {
        name: 'ProductCard',
}
</script>

<style lang="scss">
.card_wrapper{     
        width: 332px;
        height: 423px;
        background: #FFFEFB;
        box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
        border-radius: 4px;
        display: inline-flex;
        flex-direction: column;
}

.card_wrapper:hover{
        cursor: pointer;
}

.card_wrapper h3{
        margin: 0;
        font-weight: 600;
        font-size: 20px;
        line-height: 25px;
}

.img_wrapper{
        height: 200px;
        display: inline-block;
        overflow: hidden;
        // background-color: red;
}

.img_wrapper img{
        width: auto;
        max-width: 100%;
        border-radius: 4px 4px 0px 0px;
        object-fit: cover;
}

.text_wrapper{
        padding:  16px 16px 24px 16px;
        height: auto;
        flex-grow: 1;
}

.description{
        overflow: auto;
        height: 80px;
        margin: 16px 0 32px 0;
}

.price{
        height: 30px;
        font-weight: 600;
        font-size: 24px;
        line-height: 30px;
}
</style>