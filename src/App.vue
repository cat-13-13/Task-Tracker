<template>
  <div class="container">
    <HeaderTitle @toggle-add-task="toggleAddTask" title='Task Tracker' :showAddTask="showAddTask" />

    <div v-show="showAddTask">
      <AddTask @add-task="addTask"/>
    </div>
    
    <TaskBox @delete-task="deleteTask" @toggle-reminder="toggleReminder" :tasks='tasks' />
  </div>

</template>

<script>
import HeaderTitle from './components/Header.vue'
import TaskBox from './components/TaskBox.vue'
import AddTask from './components/AddTask.vue'

  export default {
    name: 'App',
    components: {
      HeaderTitle,
      TaskBox,
      AddTask
    },
    data() {
      return {
        tasks: [],
        showAddTask: false
      }
    }, 
    created(){
      this.tasks = [
        {
          id: 1,
          text: 'Doctors Appointment',
          day: 'Next thursday at 09:15',
          reminder: true
        },
        {
          id: 2,
          text: 'Cinema: Barbie',
          day: 'Saturday 22 at 18:15',
          reminder: true
        },
        {
          id: 3,
          text: 'Personal training',
          day: 'Thursday at 07:30',
          reminder: false
        }
      ]
    },
    methods:{
      addTask(task){
        this.tasks = [...this.tasks, task]
      },
      deleteTask(id){
        if (confirm('Are you sure you want to delete this task?')){
          this.tasks = this.tasks.filter(task => task.id != id)
        }
      },
      toggleReminder(id){
        this.tasks = this.tasks.map(task => {
          return task.id == id ? {...task, reminder: !task.reminder} : task
        })
      },
      toggleAddTask() {
        this.showAddTask = !this.showAddTask
      }
    }
  }

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
