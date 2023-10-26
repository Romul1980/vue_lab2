<script setup>

import {ref} from "vue";
const items = ref([
  {name: 'Buy groceries for next week', progress: 'In progress'},
  {name: 'Renew car insurance', progress: 'In progress'},
  {name: 'Sign up for online course', progress: 'In progress'}
  ]);

const handleAddTask = () =>{

  let text = document.getElementById("form1").value;
  if (text != null){
    if (text == ''){
       text = 'Something'
    }
    items.value.push({name: text, progress: 'In progress'})
  }

}
</script>
<template>
  <div class="row row-cols-lg-auto g-3 justify-content-center align-items-center mb-4 pb-2">
    <div class="col-12">
      <div class="form-outline">
        <input type="text" id="form1" class="form-control"/>
        <label class="form-label" for="form1">Enter a task here</label>
      </div>
    </div>

    <div class="col-12">
      <button type="submit" class="btn btn-primary" @click="handleAddTask()">Save</button>
    </div>

  </div>
  <table class="table mb-4">
    <thead>
    <tr>
      <th scope="col">No.</th>
      <th scope="col">Todo item</th>
      <th scope="col">Status</th>
      <th scope="col">Actions</th>
    </tr>
    </thead>
    <tbody>
      <tr v-for="(item, id) of items" :key="items">
        <td> {{id + 1}} </td>
        <td> {{item.name}} </td>
        <td> {{item.progress}} </td>
        <td>
          <button type="submit" class="btn btn-danger" @click="items.splice(id,1)">Delete</button>
          <button type="submit" class="btn btn-success ms-1" @click="items[id].progress = 'Finished'">Finished</button>
        </td>
      </tr>
    </tbody>
  </table>


</template>
<script>
export default {
  name: 'Items'
}
</script>