<template>
    <li>
        <span>
            <input type="checkbox" v-model="item.checked" >
            <span :class="todoItemStyle(item.checked)">{{item.value}}</span>
        </span>
    </li>
</template>

<script>
export default {
    props: {
        item: Object
    },
    methods:{
        todoItemStyle(checked){
            return checked ? "itemChecked" : "";
        }
    }
}
</script>

<style>
    .itemChecked{
        text-decoration: line-through;
        color: #c2c2c2;
    }
</style>