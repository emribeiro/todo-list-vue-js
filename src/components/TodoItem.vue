<template>
    <li>
        <span>
            <input type="checkbox" v-model="item.checked" >
            <span :class="todoItemStyle(item.checked)">{{item.value}}</span>
        </span>
        <span v-html="deleteIcon" @click="deleteItem"></span>
    </li>
</template>

<script>

import feather from 'feather-icons';

export default {
    props: {
        item: Object
    },
    methods:{
        todoItemStyle(checked){
            return checked ? "itemChecked" : "";
        },
        deleteItem(index){
            return this.$emit("todo-list", index);
        }
    },
    computed: {
        deleteIcon(){
            return feather.icons.trash.toSvg();
        }
    }
}
</script>

<style scoped>
    .itemChecked{
        text-decoration: line-through;
        color: #c2c2c2;
    }

    li{
        padding: 8px 0;
    }

    li, li span{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>