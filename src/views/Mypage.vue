<template>
<div class="mypage">
<h1>add todo page.</h1>
<b-form-group>
<b-row class='mt-4'>
<b-col sm='6' offset='3'>
<b-form-input type="text" v-model='newTask'></b-form-input>
</b-col>
<b-col sm='1'>
<b-button @click="addTask()">add</b-button>
</b-col>
</b-row>
</b-form-group>
<div>
<b-card v-for="(task, key) in tasks" :key='key' :class="statusColor(task.status)">
<template v-if="task.edit">
  <b-row class='mt-4'>
  <b-col sm='6' offset='3'>
  <b-form-input type="text" v-model='task.name'></b-form-input>
  </b-col>
  <b-col sm='1'>
  <b-button @click="editTask(key)">edit</b-button>
  </b-col>
  </b-row>
</template>
<h3 class="card-title" v-else @click="taskEdit(key)">{{ task.name }}</h3>

<b-form-checkbox v-model="task.status" value="done" unchecked-value="yet">{{ task.status }}</b-form-checkbox>
</b-card>
</div>
</div>
</template>

<style>
.green.card {
background: #c5e8d7;
}

.grey.card {
background: #d6d6d6;
}

.card-title {
    transition: .5s;
  }

.card-title:hover {
    opacity: 0.5;
}
</style>

<script>
export default {
name: 'Mypage',
        data: function(){
          return {
newTask: '',
         tasks: [
         ]
          }
        },
methods: {
addTask: function(){
           var newTask = { name: this.newTask, status: 'yet', edit: false };
           this.newTask = '';
           this.tasks.unshift(newTask);
         },
statusColor: function(status){
               return {
                 'grey': status == 'done',
                 'green': status == 'yet',
               }
             },
taskEdit: function(id){
  this.tasks[id].edit = true;
          },
editTask(id){
           this.tasks[id].edit = false
         },
         },
         }
</script>
