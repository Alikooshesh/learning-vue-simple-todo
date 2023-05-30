<script>
import AddTodoBox from './components/AddTodoBox.vue';

export default {
  components : {
    AddTodoBox
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
    
    <div class="w-full mt-[16px] ">
      <AddTodoBox :addTodoFunction="addTodo" />
    </div>
  </div>
</template>

