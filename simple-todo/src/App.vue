<script>
import AddTodoBox from './components/AddTodoBox.vue';
import TodoCard from './components/TodoCard.vue';
import EditTodoBox from './components/EditTodoBox.vue';

export default {
  components : {
    AddTodoBox,
    TodoCard,
    EditTodoBox
  },
  data() {
    return {
      todoList : [
        {
          id : 0,
          todo : "test",
          isDone : false
        }
      ],
      editMode : {
        status : false,
        todoId : null
      }
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
      this.editMode = {
        status : true,
        todoId
      }
      console.log(this.editMode)
    },
    updateTodo(todoId,newTodoText){
      this.todoList.find(item => item.id === todoId).todo = newTodoText
      this.editMode.status = false
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
      <EditTodoBox v-if="editMode.status" 
      :id="editMode.todoId" 
      :prevTodoText="todoList.find(item=> item.id === editMode.todoId).todo"
      :updateTodoFunction="updateTodo"
      />
      <AddTodoBox v-else :addTodoFunction="addTodo" />
    </div>

    <div class="w-full py-[16px] flex flex-col gap-[8px]">
      <div class="w-full" v-for="todo in todoList" :key="todo.id">
        <TodoCard :id="todo.id" :title="todo.todo" :deleteFunction="deleteTodo" :editFunction="editTodo"/>
      </div>
    </div>
  </div>
</template>

