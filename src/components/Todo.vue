<template>
  <div>
  <h1>
  To Do
  </h1>
  <h2>
  Add Task
  </h2>
  <form @submit.prevent="addTask()">
  <input required ref="input" type="text" placeholder="add task..." v-model="task"  />
  <button type="submit">add</button>
  <button @click="task=''">clear</button>
  </form>

  <h2>
  Pending Task
  </h2>
   <ul>
    <li v-for="(item, i) in pendingTask" :key="i">{{item}} <button @click="task=''">done</button></li>   
  </ul>

  <h2>
  Completed Task
  </h2>
   <ul>
    <li v-for="(item, i) in pendingTask" :key="i">{{item}} <button @click="task=''">done</button></li>   
  </ul>
  
    
  </div>
</template>

<script>
export default {
  name: 'Todo',
  props: {
    msg: String
  },
  data(){
      return {
          pendingTask:[],
          task:''
      }
  },
  methods:{
      addTask(){
          this.pendingTask.push(this.task);
          this.task=''
      }
  }
}
</script>
<style scoped>

</style>
