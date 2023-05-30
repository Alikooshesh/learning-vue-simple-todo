<script>
    export default{
        props:{
            addTodoFunction : {
                type : Function,
                required : true
            }
        },
        data(){
            return{
                newTodoInputValue : ""
            }
        },
        methods:{
            handleClick(){
                if(this.newTodoInputValue.length < 1) return

                this.addTodoFunction(this.newTodoInputValue)
                this.newTodoInputValue = ""
            }
        }
    }
</script>

<template>
    <div class="w-full h-[40px] px-[8px] py-[4px] flex flex-col md:flex-row items-center gap-[8px]">
        <input v-model="newTodoInputValue" placeholder="Meet Ali or etc ..." class="w-full min-h-[40px] px-[8px] bg-[rgb(210,200,200)] border-none outline-none rounded-[8px] text-gray-700 text-[20px] placeholder:text-gray-500"/>
        <button @click="handleClick()" class="p-[8px] max-h-[40px] bg-[rgb(210,200,200)] text-black text-[32px] rounded-[8px] flex items-center justify-center">+</button>
    </div>
</template>