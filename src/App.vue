<template>
  <div class="container">
    <HeaderComponent title="Task Tracker" @toggle-add-task="toggleAddTask" :showAddTask= "showAddTask"/>
    <div v-show="showAddTask">
      <!-- <div v-if="showAddTask"> -->
      <AddTaskComponent @add-task="addTask" />
    </div>

    <TasksComponent @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>


</template>

<script>
import HeaderComponent from './components/Header'
import TasksComponent from './components/Tasks'
import AddTaskComponent from './components/AddTask'
export default {
  name: 'App',
  components: {
    HeaderComponent,
    TasksComponent,
    AddTaskComponent
  },
  data() {
    return {
      tasks: [],
      showAddTask: false
    }
  },

  methods: {
    deleteTask(id) {
      // filter: we want back everything apart from the task with id being parsed

      if (confirm('Are you sure?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      // console.log(id)
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      )
    },
    addTask(task) {
      // spread across the previous array and add the new task
      this.tasks = [...this.tasks, task]
    },
    toggleAddTask (){
      this.showAddTask = !this.showAddTask

    },
   
  },

  // this is where you will make http requests, if you want to load some data
  // on your page when your components loads
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Doctors Appointment',
        day: 'March 1st at 2:30pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Peer Meeting',
        day: 'March 2st at 2:30pm',
        reminder: true,
      },
      {
        id: 3,
        text: 'Tailors Appointment',
        day: 'March 3st at 2:30pm',
        reminder: false,
      }
    ]
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
