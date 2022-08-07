<template>
        <div class="dropdown">
                <button class="dropdown_btn"> <span>{{modelValue.name}}</span><i class="arrow down"></i> </button>
                <div class="dropdown_content" >
                        <p 
                                v-for="option of getUnchangedVal" :key="option.value"
                                @click="changeActiveValue(option)"
                        >
                                {{option.name}}
                        </p>
                </div>
        </div>
</template>

<script>
import _cloneDeep from 'lodash.clonedeep';

export default {
        props:{
                modelValue: {
                        type: Object,
                },
                options: {
                        type: Array,
                },
        },
        computed: {
                getUnchangedVal(){
                        let newOptions = _cloneDeep(this.$props.options);
                        return newOptions.filter((i)=> i.value != this.$props.modelValue.value)
                }

        },
        methods:{
                changeActiveValue(val){
                        this.$emit('update:modelValue', val)
                }
        }
}
</script>

<style scoped lang="scss">
@import "@/styles/variables.scss";

.dropdown {
        position: relative;
        display: inline-block;
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 400;
        font-size: 12px;
        line-height: 15px;
}

.dropdown_btn {
        border: none;
        height: 36px;
        padding: 10px 16px 11px 16px;
        box-shadow: 0px 2px 5px $def_shadow_color;
        border-radius: 4px;
        background: $bg_color;
        display: flex;
        align-items: center;
        color: $sort_select_color;
        cursor: pointer;

        span{
                min-width: 78px;
                margin-right: 5px;
        }

        i {
                border: solid $sort_select_color;
                border-width: 0 1px 1px 0;
                display: inline-block;
                width: 4.59px;
                height: 4.59px;
                transform: rotate(45deg);
        }
}

.dropdown_content {
        display: none;
        position: absolute;
        right: 0;
        background-color: $bg_color;
        min-width: 150px;
        box-shadow: 0px 8px 16px 0px $def_shadow_color;
        z-index: 1;
        border-radius: 4px;
        padding: 0px;

        p {
                color: $sort_select_color;
                padding: 12px 16px;
                display: block;
                margin: 0px;
        }

        p:first-of-type{
                border-top-left-radius: 4px;
        }

        p:last-of-type{
                border-bottom-left-radius: 4px;
        }

        p:hover {
                background: $sort_bg_color;
                cursor: pointer;
        }
}

.dropdown:hover {
        .dropdown_content  {
                display: block;
        }
}
</style>

