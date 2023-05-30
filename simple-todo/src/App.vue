<script>
import AddTodoBox from './components/AddTodoBox.vue';
import TodoCard from './components/TodoCard.vue';

export default {
  components : {
    AddTodoBox,
    TodoCard
  },
  data() {
    return {
      todoList : [
        {
          id : 0,
          todo : "test",
          isDone : false
        }
      ]
    }
  },
  methods : {
    addTodo(todoText){
      if (todoText.length < 1) return

      const newTodo = {
        id : Date.now(),
        todo : todoText,
        isDone : false
      }
      
      this.todoList.push(newTodo)
    },
    deleteTodo(todoId){
      this.todoList = this.todoList.filter(item => item.id !== todoId)
    },
    editTodo(todoId){
      console.log(todoId)
    }
  }
}

</script>

<template>
  <div class="w-full max-w-[90%] sm:max-w-[600px] mx-auto pt-[48px]">
    <div class="w-full flex items-start justify-between">
      <h1 class="text-[72px] font-bold">Todos</h1>
      <div class="mt-[40px] flex flex-col gap-4px font-bold gap-[4px]">
        <div class="flex items-end gap-[4px]">
          <p class="text-[40px]">{{ todoList.filter(item => item.isDone).length }}</p>
          <p class="text-[20px]">Comp.</p>
        </div>
        <div class="flex items-end gap-[4px]">
          <p class="text-[40px]">{{ todoList.length }}</p>
          <p class="text-[20px]">Total</p>
        </div>
      </div>
    </div>
    
    <div class="w-full py-[16px] border-b border-black">
      <AddTodoBox :addTodoFunction="addTodo" />
    </div>

    <div class="w-full py-[16px] flex flex-col gap-[8px]">
      <div class="w-full" v-for="todo in todoList">
        <TodoCard :id="todo.id" :title="todo.todo" :deleteFunction="deleteTodo"/>
      </div>
    </div>
  </div>
</template>

