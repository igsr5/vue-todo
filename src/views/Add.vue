<template>
  <div class="about">
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
    <b-card v-for="(task, key) in tasks" :key='key' :title="task.name">
    <b-form-checkbox v-model="task.status" value="done" unchecked-value="yet">{{ task.status }}</b-form-checkbox>
    </b-card>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Add',
    data: function(){
        return {
          newTask: 'test',
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
          }
      }
}
</script>
