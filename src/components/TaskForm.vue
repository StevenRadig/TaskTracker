<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Task</label>
            <input type="text" v-model="text" name="text" placeholder="Add Task" />
        </div>
        <div class="form-control">
            <label>Day and Time</label>
            <input type="text" v-model="day" name="day" placeholder="Add Day & Time" />
        </div>
        <div class="form-control">
            <label>Set Reminder</label>
            <input type="checkbox" v-model="reminder" name="reminder" />
        </div>

        <input type="submit" value="Save Task" class="btn">
    </form>
</template>

<script>
     export default {
         name: 'TaskForm',
         data() {
             return {
                 text: '',
                 day: '',
                 reminder: false,
             }
         },
         methods: {
             onSubmit(e) {
                 e.preventDefault()

                 if(!this.text) {
                     alert('Cannot create empty task')
                     return
                 }

                 const newTask = {
                    //  id: Math.floor(Math.random() * 100000),
                     text: this.text,
                     day: this.day,
                     reminder: this.reminder,
                 }
                 this.$emit('add-task', newTask)

                 this.text = ''
                 this.day = ''
                 this.reminder = false
             }
         }
     }
</script>