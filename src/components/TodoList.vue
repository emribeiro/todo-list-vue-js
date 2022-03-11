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
      },
      removeTodoItem(index){
        this.list.splice(index, 1);
        localStorage.setItem('todolist', JSON.stringify(this.list));
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
        @todo-list="removeTodoItem"
      />
    </ul>
  </div>
</template>

<style scoped>
  ul{
    list-style: none;
    padding: 0;
  }

  .container{
    width: 500px;
    margin: auto;
  }

  .container input{
    width: 80%;
    height: 32px;
  }

  .container ul{
    width: 80%;
    margin: 20px auto;
    text-align: left;
  }

</style>
