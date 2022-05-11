<template>
  <div>
    <h1>Todo List</h1>
  </div>

  <div class="formsection">

    <form >
          <input type="text" v-model="task" >
          <input type="date" v-model="date" >
          <select v-model="priority">
            <option selected disabled="disabled" value="">Priority</option>
            <option>Critical</option>
            <option>High</option>
            <option>Low</option>
          </select>
          <button @click.prevent="saveItem">Save</button>

          
      </form>

   
  </div>

<div class="taskSection">
  <div v-for="(eachTask, index) in allTask" :key="index" class='taskContainer'>
    <div>
      
      <p>{{eachTask.event}}</p>
      <p>{{eachTask.status}}</p>
    </div>
    <div>

      <p>{{eachTask.completedby}}</p>
      <p>{{eachTask.deadline}}</p>
    </div>
    <div>

      <p v-if="eachTask.event"><i class="ri-edit-line"></i></p>
      <p v-if="eachTask.event"><i @click="deleteItem(index)" class="ri-delete-bin-6-line"></i></p>
    </div>
  </div>
  
</div>

</template>

<script> 
export default {
  data() {
    return{
      task: '',
      status: '',
      date: '',
      priority: '',
      // todoPresent: false,

      allTask: [
       ]

    }
  },

  methods:{
    saveItem(){
      if(this.task.length===0) return ;{
        this.allTask.push({
          event:this.task,
          status:'todo',
          deadline:this.date,
          completedby:this.priority,
          
        });
      }

      // this.todoPresent=!this.todoPresent
    },

    deleteItem(index){
       console.log(`deleteButton number ${index}`)
       this.allTask.splice(index, 1);
      }
      
    
  }

  }

</script>
  
<style>
.taskSection{
  display: flex;
  align-items: center;
  flex-direction: column;
  margin-top: 20px;
}
.taskContainer{
  height: 100px;
  width: 500px;
  color: white;
  background-color: purple;
  border-radius: 10px;
  margin-bottom: 15px;
  padding-left: 8px;
  display:  flex;
  justify-content: space-around;
  align-items: center;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.15);
  

}
.formsection{
  display: flex;
  justify-content: center;
}
</style>