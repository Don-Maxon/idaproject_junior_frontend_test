<template>
        <select name="sort_select" id="sort_select" @change="changeSortValue">
                <option value="def">По умолчанию</option>
                <option value="min">По цене min</option>
                <option value="max">По цене max</option>
                <option value="name">По наименованию</option>
        </select>
</template>

<script>
export default {
        name: 'SortSelect',
        props: {
                modelValue: String,
        },
        methods:{
                changeSortValue(event){
                        this.$emit('update:modelValue', event.target.value)
                }
        }
}
</script>

<style lang="scss">
@import "@/styles/variables.scss";

#sort_select{
        border: none;
        width: auto;
        height: 36px;
        padding: 10px 0px 11px 16px;
        background: $bg_color;
        box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
        border-radius: 4px;
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 400;
        font-size: 12px;
        line-height: 15px;
        color: $sort_select_color;
        cursor: pointer;
}

#sort_select:active, #sort_select:focus{
  outline:none;
}




</style>