<template>
  <li class="box" @dragover="allowDrag" @dragenter="dragenter" @drop="drop">
    <div class="box-title">{{title}}</div>
    <slot></slot>
  </li>
</template>
<script>
  export default {
    name: 'box',
    props: ['title', 'index'],
    methods: {
      dragenter (ev) {
        ev.dataTransfer.dropEffect = 'move'
        ev.preventDefault()
      },
      allowDrag (ev) {
        ev.preventDefault()
      },
      drop (ev) {
        let dragBoxIndex = ev.dataTransfer.getData('index')
        let dragBoxInnerIndex = ev.dataTransfer.getData('innerIndex')
        ev.preventDefault()
        this.$emit('dragChange', this.index, dragBoxIndex, dragBoxInnerIndex)
      }
    }
  }
</script>
<style lang="css">
.box{
  list-style:none;
  height: 100%;
  overflow-y: auto;
  width: 280px;
  margin-right: 10px;
  padding: 10px;
  background-color: #EEEEEE;
  float:left;
}
.box-title{
  text-indent: 24px;
  font-size: 16px;
  font-weight: 600;
  height: 40px;
  line-height: 40px;
} 
</style>
