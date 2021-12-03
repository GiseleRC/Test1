<template>
  <div class="container" >
    <h2 class="text-center mt-5">My vue todo app</h2>

    <!-- inputs -->
    <div class="d-flex">
      <input v-model="task" type="text" placeholder="Enter task" class="form-control">
      <button @click="submitTask" class="btn btn-warning rounded-0">Submit</button>
    </div>
    <!-- task tab -->
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col" class="text-center">Task</th>
          <th scope="col" class="text-center">Status</th>
          <th scope="col" class="text-center">Edit</th>
          <th scope="col" class="text-center">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td>
            <span :class="{'finished': task.status === 'finished'}">{{task.name}}</span>
          </td>
          <td style="width: 120px">
            <span @click="changeStatus(index)" class="pointer">
              {{firstCharUpper(task.status)}}
            </span>
          </td>
          <td>
            <div class="text-center" @click="editTask(index)">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center" @click="deleteTask(index)">
              <span class="fa fa-trash"></span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },

  data(){
    return {
      task: '',
      editedTask: null,
      availableStatusses: ['to-do', 'in-progress', 'finished'],

      tasks: [
        {
          name: 'Go to the market',
          status: 'To-do',
          },
        {
          name: 'Go to the bed',
          status: 'In-progres',
        }
      ]
    }
  },

  methods: {
    submitTask(){
      if(this.task.lenth === 0) return;

      if(this.editedTask === null){
          this.tasks.push({
          name: this.task, 
          status: 'to-do'
        });
      }else{
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }

      this.task = '';
    },
  
    deleteTask(index){
      this.tasks.splice(index, 1);
    },

    editTask(index){
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },

    changeStatus(index){
      let newIndex = this.availableStatusses.indexOf(this.tasks[index].status);
      if(++newIndex > 2) newIndex = 0;
      this.tasks[index].status = this.availableStatusses[newIndex];
    },
    firstCharUpper(str){
      return str.charAt(0).toUpperCase() + str.slice(1);
    }
  }
};
</script>
<!-- coment -->
<style scoped> 
  .pointer {
    cursor: pointer;
  }
  .finished {
    text-decoration: line-through;
  }
</style>
