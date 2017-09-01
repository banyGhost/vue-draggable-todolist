<template>
  <div id="app">
    <Container>
      <Box v-for="(item, index) in taskList" :key="index"
      @dragChange="dragChange" :title="item.title" :index="index">
        <Card v-for="(innerItem, innerIndex) in item.tasks" :key="index + '-' + innerIndex" 
        :data="innerItem" :innerIndex="innerIndex" :index="index"></Card>
      </Box>
    </Container>
  </div>
</template>

<script>
import Container from './components/Container'
import Box from './components/Box'
import Card from './components/Card'
export default {
  name: 'app',
  components: {
    Container,
    Box,
    Card
  },
  data () {
    return {
      taskList: [{
        title: '待完成',
        tasks: [{
          content: '数学作业',
          targetTime: '2017-08-31'
        }, {
          content: '语文作业',
          targetTime: '2017-09-01'
        }]
      }, {
        title: '已经完成',
        tasks: [{
          content: '物理作业',
          targetTime: '2017-07-31'
        }, {
          content: '英语作业',
          targetTime: '2017-08-01'
        }]
      }, {
        title: '做完了，但是不合格的',
        tasks: [{
          content: '化学作业',
          targetTime: '2017-07-30'
        }, {
          content: '生物',
          targetTime: '2017-09-01'
        }]
      }]
    }
  },
  methods: {
    dragChange (index, changeIndex, changeInnerIndex) {
      let a = this.taskList[changeIndex].tasks.splice(changeInnerIndex, 1)
      this.taskList[index].tasks.push(a[0])
      console.log(this.taskList)
    }
  }
}
</script>

<style>
* {
  margin:0px;
  padding: 0px;
  box-sizing: border-box;
}
html,body{
  height: 100%;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  height: 100%;
}
</style>
