<template>
<div class="h-full w-full flex items-center p-4 bg-green-500" :class="error && 'fail' || 'success'">
    <h3 class="text-dark-200 ml-1">{{msg}}</h3>
</div>
</template>

<style>
  .fail{
    background-color: rgb(255, 75, 75);
  }
  .success{
    background-color: rgb(103, 255, 95);
  }
</style>

<script>
  export default{
      name : 'NotiFications',
      props : {
        msg : {
          type : String
        },
        error : {
          type : Boolean
        }
      }
  }
</script>