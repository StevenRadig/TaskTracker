<template>
  <main class="view__home">
      <!-- App title and button to add a new task with the task form -->
      <Header title="Task Tracker" @toggle-add-task="toggleAddTask" :showAddTask="showAddTask"/>

    <!-- Conditionally visible form to add new task -->
    <div v-show="showAddTask">
      <TaskForm @add-task="addTask"/>
    </div>

    <!-- List of tasks -->
    <Tasks :tasks="tasks"
      @toggle-reminder="toggleReminder" 
      @delete-task="deleteTask" 
    />
  </main>
</template>

<script>
  import Header from '../components/Header'
  import TaskForm from '../components/TaskForm'
  import Tasks from '../components/Tasks'
  
  export default {
    name: 'Home',
    components: {
      Header,
      TaskForm,
      Tasks,
    },
    data() {
      return {
        tasks: [],
        showAddTask: false,
      }
    },
    methods: {
      // toggle visibility of form to add task
      toggleAddTask() {
        this.showAddTask = !this.showAddTask
      },
      async addTask(task) {
        const res = await fetch('api/tasks', {
          method: 'POST',
          headers: {
            'Content-type': 'application/json'
          },
          body: JSON.stringify(task)
        })
        const data = await res.json();
        this.tasks = [...this.tasks, data]
      },
      
      async deleteTask(id) {
        if (confirm('Are you sure?')) {
          const res = await fetch(`api/tasks/${id}`, {
            method: 'DELETE'
          })

          res.status === 200 ? (this.tasks = this.tasks.filter((task) => task.id !== id)) : alert('Error deleting task')
        }
      },

      async toggleReminder(id) {
        const taskToToggle = await this.fetchTask(id)
        const updTask = {...taskToToggle, reminder: !taskToToggle.reminder}

        const res = await fetch(`api/tasks/${id}`, {
          method: 'PUT',
          headers: {
            'Content-type': 'application/json',
          },
          body: JSON.stringify(updTask)
        })

        const data = await res.json()
        
        this.tasks = this.tasks.map((task) => 
          task.id === id ? {...task, reminder: data.reminder} : task
        )
      },

      async fetchTasks() {
        const res = await fetch('api/tasks')

        const data = await res.json()

        return data
      },
      async fetchTask(id) {
        const res = await fetch(`api/tasks/${id}`)

        const data = await res.json()

        return data
      }
    },
    async created() {
      this.tasks = await this.fetchTasks()
    }
  }
</script>