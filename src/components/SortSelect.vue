<template>
        <select name="sort_select" id="sort_select">
                <option selected value="">По умолчанию</option>
                <option value="">По цене min</option>
                <option value="">По цене max</option>
                <option value="">По наименованию</option>
        </select>
</template>

<script>
export default {
        name: 'SortSelect',

}
</script>

<style lang="scss">
#sort_select{
        border: none;
        width: auto;
        height: 36px;
        padding: 10px 0px 11px 16px;
        background: #FFFEFB;
        box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
        border-radius: 4px;
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 400;
        font-size: 12px;
        line-height: 15px;
        color: #B4B4B4;
        cursor: pointer;
        
}

#sort_select:active, #sort_select:focus{
  outline:none;
  outline-color: red;
}




</style>