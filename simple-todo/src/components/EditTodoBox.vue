<script>
    export default{
        props:{
            id:{
                type : Number,
                required : true
            },
            prevTodoText : {
                type: String
            },
            updateTodoFunction : {
                type : Function,
                required : true
            }
        },
        data(){
            return{
                updatedTodoInputValue : ""
            }
        },
        methods:{
            handleClick(){
                if(this.updatedTodoInputValue.length < 1) return

                this.updateTodoFunction(this.id,this.updatedTodoInputValue)
                this.updatedTodoInputValue = ""
            }
        },
        mounted(){
            this.updatedTodoInputValue = this.prevTodoText ?? ""
        },
        updated(){
            this.updatedTodoInputValue = this.prevTodoText ?? ""
        }
    }
</script>

<template>
    <div class="w-full h-[40px] px-[8px] py-[4px] flex flex-col md:flex-row items-center gap-[8px]">
        <input v-model="updatedTodoInputValue" class="w-full min-h-[40px] px-[8px] bg-[rgb(210,200,200)] border-none outline-none rounded-[8px] text-gray-700 text-[20px] placeholder:text-gray-500"/>
        <button @click="handleClick()" class="p-[8px] max-h-[40px] bg-[rgb(210,200,200)] text-black text-[32px] rounded-[8px] flex items-center justify-center">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" class="bi bi-check-lg" viewBox="0 0 16 16">
  <path d="M12.736 3.97a.733.733 0 0 1 1.047 0c.286.289.29.756.01 1.05L7.88 12.01a.733.733 0 0 1-1.065.02L3.217 8.384a.757.757 0 0 1 0-1.06.733.733 0 0 1 1.047 0l3.052 3.093 5.4-6.425a.247.247 0 0 1 .02-.022Z"/>
</svg>
        </button>
    </div>
</template>