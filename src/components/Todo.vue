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
  <button style="margin-left:4px;" type="submit">add</button>
  <button style="margin-left:4px;"  @click="task=''">clear</button>
  </form>

  <h2>
  Pending Task
  </h2>
   <ol>
    <div v-for="(item, i) in pendingTask" :key="i">
    <div style="display:inline-flex; justify-content:center; margin-bottom:8px;">
    <li>{{item}}</li> <button  style="margin-left:4px;" @click="moveTodDone(item)">done</button> 
    </div>
     </div> 
  </ol>


  <h2>
  Completed Task
  </h2>
   <ul>
    <li v-for="(item, i) in completedTask" :key="i">{{item}} <button @click="clearCompletedTask(item,i)">clear</button></li>   
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
          completedTask:[],
          task:''
      }
  },
  methods:{
      addTask(){
          this.pendingTask.push(this.task);
          this.task=''
      },
      moveTodDone(item){
        let idx=this.pendingTask.findIndex(x=>x===item);
         this.pendingTask.splice(idx,1);
         this.completedTask.unshift(item);
         this.task='';
      },
      clearCompletedTask(item,i){
        this.completedTask.splice(i,1);
      }

  }
}
</script>
<style scoped>

</style>
