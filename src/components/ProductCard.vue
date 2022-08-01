<template>
        <div class="card_wrapper">
                <div class="delete_icon" @click="deleteItem">
                        <img src="../assets/pages/trash_item.png" alt="">
                </div>
                <div class="img_wrapper"> 
                        <img :src="img_url" alt="Изображение товара" >
                </div>
                <div class="text_wrapper"> 
                        <h3>{{titel}}</h3>
                        <div class="description">
                                {{description}}
                        </div>
                        <div class="price">{{price}} <span>руб.</span></div>
                </div>
        </div>
</template>

<script>
export default {
        name: 'ProductCard',
        data() {
                return { }      
        
        },
        props: {
                img_url: {
                        type: String,
                        default: require('../assets/pages/no_img.png')
                },
                titel: {
                        type: String,
                        default: "..."
                },
                description:{
                        type: String,
                        default: "..."
                },
                price:{
                        type: String,
                        default: "1"
                }
        },
        methods:{
                deleteItem(){
                        console.log('delete');
                }
        }
}
</script>

<style lang="scss">
.card_wrapper{    
        position: relative; 
        width: 332px;
        height: 423px;
        background: #FFFEFB;
        box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
        border-radius: 4px;
        display: inline-flex;
        flex-direction: column;
        visibility: visible;
}

.card_wrapper:hover{
        cursor: pointer;
}

.card_wrapper:hover .delete_icon{
        visibility: visible;
        opacity: 1;
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
        overflow: hidden;
        text-overflow: ellipsis;
        -webkit-line-clamp: 3;
        height: 80px;
        margin: 16px 0 32px 0;
}

.price{
        height: 30px;
        font-weight: 600;
        font-size: 24px;
        line-height: 30px;
}

.delete_icon{
        right: -8px;
        top: -8px;
        position: absolute;
        width: 32px;
        height: 32px;
        background: #FF8484;
        box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
        border-radius: 10px;
        display: flex;
        align-items: center;
        justify-content: center;
        visibility: hidden;
        opacity: 0;
        transition: background .5s, opacity .5s;
        // transition: 1s opacity;

   
}

.delete_icon:hover{
        cursor: pointer;
        background: #ed2121;
        visibility: hidden;
        opacity: 1;       
}
</style>