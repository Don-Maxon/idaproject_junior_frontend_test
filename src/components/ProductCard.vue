<template>
        <div class="card_wrapper">
                <div class="delete_icon" @click="dleteCardItem">
                        <img src="../assets/pages/trash_item.png" alt="">
                </div>
                <div class="img_wrapper"> 
                        <img :src="img_url" alt="Изображение товара" >
                </div>
                <div class="text_wrapper"> 
                        <h3>{{titel}}</h3>
                        <div class="description_wrapper">
                                <div class="description">
                                        {{description}}
                                </div>
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
                },
                id:{
                        type: String,
                        required: true
                }
        },
        methods:{
                dleteCardItem(){
                        this.$emit("dleteCardItem", this.$props.id)
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
        margin-left: 16px;
        margin-bottom: 16px;
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
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
}

.img_wrapper{
        max-height: 200px;
        max-height: 200px;
        display: inline-block;
        overflow: hidden;
        display: flex;
        justify-content: center;
}

.img_wrapper img{
        height: 100%;
        width: auto;
        max-width: 100%;
        border-radius: 4px 4px 0px 0px;
        object-fit: cover;
        min-height: 200px;
}

.text_wrapper{
        padding:  16px 16px 24px 16px;
        height: auto;
        flex-grow: 1;
        display: flex;
        flex-direction: column;
}

.description_wrapper{
        flex-grow: 1;
}

.description{ 
        overflow: hidden;
        text-overflow: ellipsis;
        height: auto;
        margin: 16px 0 32px 0;
	display: -webkit-box;
	-webkit-line-clamp: 4;
	-webkit-box-orient: vertical;
        
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
}

.delete_icon:hover{
        cursor: pointer;
        background: #ed2121;
        visibility: hidden;
        opacity: 1;       
}

@media (max-width: 768px){
        .card_wrapper{
                margin-left: 0;
                height: auto;
        }
        
        .description{
                margin: 8px 0;
        }
}

@media (max-width: 700px){
        .card_wrapper{
                width: 100%;
        }
}
</style>