<template>
  <div class="container" >
    <h2 class="text-center mt-5">My vue todo app</h2>

    <!-- inputs -->
    <div class="d-flex">
      <input type="text" placeholder="Enter task" class="form-control">
      <button class="btn btn-warning rounded-0">Submit</button>
    </div>
    <!-- task tab -->
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col" class="text-center">Task</th>
          <th scope="col" class="text-center">Status</th>
          <th scope="col">Edit</th>
          <th scope="col">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td>{{task.name}}</td>
          <td>{{task.status}}</td>
          <td>
            <div class="text-center">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center">
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
  }
}
</script>


<style scoped>

 
</style>
