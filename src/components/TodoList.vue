<script>

  import TodoItem from "./TodoItem.vue";

  export default{
    components: {
      TodoItem
    },
    data(){
      return {
        list: JSON.parse(localStorage.getItem('todolist') || '[]')
      }
    },
    methods: {
      addTodoItem(event){
          this.list.unshift({
            value: event.target.value,
            checked: false
          });

          localStorage.setItem('todolist', JSON.stringify(this.list));
          event.target.value = '';
      }
    }
  }
</script>

<template>
  <div class="container">
    <h1>TodoList</h1>
    <input type="text" @keyup.enter="addTodoItem">
    <ul>
      <TodoItem
        v-for="item, index in list"
        :key="index"
        :item="item"
      />
    </ul>
  </div>
</template>

<style scoped>
  ul{
    list-style: none;
    padding: 0;
  }
</style>
