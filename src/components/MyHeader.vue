<template>
<div class="w-full flex flex-row justify-between px-4 py-2 items-center my-2">
   <h2 class="text-center text-xl font-josefin">Task Track</h2>
   <button @click="toggleFunc" class="w-[100px] rounded-lg p-2 bg-dark-200 hover:bg-light-200 text-light-200 hover:text-dark-200 border-2 border-dark-200"><span v-if="!isOpen" class="font-josefin">Add Task</span><span v-if="isOpen" class="font-josefin">Hide</span></button>
</div>
</template>

<script>
  export default{
     name : 'MyHeader',
     props:{
        toggle : {
           type: Function
        },
        isOpen : {
           type : Boolean
        },
     },
     methods : {
        toggleFunc(){
          this.$emit('toggle');
        }
     }
  }
</script>