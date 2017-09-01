<template>
  <ul class="container">
    <slot></slot>
  </ul>
</template>
<script>
  export default {
    name: 'container'
  }
</script>
<style lang="css">
  .container{
    border: 1px solid #e9eaec;
    width: 1000px;
    height: 600px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50% ,-50%);
    overflow-x:auto;
    padding: 10px;
  }
</style>
