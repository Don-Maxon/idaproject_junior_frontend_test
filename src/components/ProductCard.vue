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

<style scoped lang="scss">
$bg_color: #FFFEFB;
$card_box_shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
$danger_color: #FF8484;
$act_danger_color: #ed2121;
$def_shadow_color: rgba(0,0,0,0.1);



.card_wrapper{    
        position: relative; 
        max-width: 332px;
        width: 100%;
        height: 423px;
        background: $bg_color;
        box-shadow: $card_box_shadow;
        border-radius: 4px;
        display: inline-flex;
        flex-direction: column;
        visibility: visible;
        margin-left: auto;

        margin-bottom: 16px;

        h3{
                margin: 0;
                font-weight: 600;
                font-size: 20px;
                line-height: 25px;
                white-space: nowrap;
                overflow: hidden;
                text-overflow: ellipsis;
        }
}

.card_wrapper:hover{
        cursor: pointer;

        .delete_icon{
                visibility: visible;
                opacity: 1;
        }
}

.img_wrapper{
        max-height: 200px;
        max-height: 200px;
        display: flex;
        
        overflow: hidden;
        justify-content: center;

        img{
                height: 100%;
                width: auto;
                max-width: 100%;
                border-radius: 4px 4px 0px 0px;
                object-fit: cover;
                min-height: 200px;
        }
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
        background: $danger_color;
        box-shadow: 0px 2px 4px $def_shadow_color;
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
        background: $act_danger_color;
        visibility: hidden;
        opacity: 1;       
}

@media (max-width: 1280px){
        .card_wrapper{
                max-width: 100%;
        }
}

@media (max-width: 768px){
        .card_wrapper{
                min-width: auto;
                height: auto;
        }
        
        .description{
                margin: 8px 0;
        }
        .img_wrapper{
                img{
                        max-height: 200px;
                        max-width: auto;
                }
        }
}

@media (max-width: 640px){
        .card_wrapper{
                min-width: 100%;
        }
}
</style>