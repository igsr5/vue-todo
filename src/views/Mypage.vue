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
<div class="mt-4">
<b-card v-for="(task, key) in tasks" :key='key' :title="task.name" :class="statusColor(task.status)">
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
         { name: 'homework', status: 'done' },
         { name: 'test', status: 'yet'},
         { name: 'shopping', status: 'done' },
         ]
          }
        },
methods: {
addTask: function(){
           var newTask = { name: this.newTask, status: 'yet' };
           this.newTask = '';
           this.tasks.unshift(newTask);
         },
statusColor: function(status){
               return {
                 'grey': status == 'done',
                 'green': status == 'yet',
               }
             },
         },
}
</script>
