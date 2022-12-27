<template>
  <dir id="app" class="app">

    <div class="hat">
      <MainHat/>
    </div>
    <div class="panel">

      <div class="create">
        <CreateTask/>
      </div>

      <div class="task">
        <Task/>
      </div>

    </div>

  </dir>
</template>

<script>
import CreateTask from './components/СreateTask.vue'
import MainHat from './components/MainHat.vue'
import Task from './components/BoardTask.vue'
//import { thisTypeAnnotation } from '@babel/types';
export default {
    name: 'app',
    components: {
      MainHat, 
      CreateTask,
      Task
    }
    
} 
</script>

<style>
.app
{
  margin: 0;
  padding: 0;
}
.panel
{
  background: #f8f9fd;
  position: relative;
}
.hat
{
  position: relative;
  display: table;
  width: 100%;
  background: white;
}
.create {
  position: relative;
  margin-bottom: 20px;
  display: table;
  width: 100%;
}
.task
{
  background: white;
}
.taskSenc
{
  background: rgb(148, 148, 148);
}
</style>
