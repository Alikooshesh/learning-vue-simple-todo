<script setup>
    defineProps({
        id : {
            type : Number
        },
        title : {
            type : String,
            required : true
        },
        isDone : {
            type : Boolean
        },
        editFunction : {
            type : Function
        },
        deleteFunction : {
            type : Function
        }
    })
</script>

<template>

</template>