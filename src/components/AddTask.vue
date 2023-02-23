<template>
    <form @submit="onSubmit" class="add-form">
      <div class="form-control">
        <label>Task</label>
        <input type="text" v-model="text" name="text" placeholder="Add Task" />
      </div>
      <div class="form-control">
        <label>Day & Time</label>
        <input
          type="text"
          v-model="day"
          name="day"
          placeholder="Add Day & Time"
        />
      </div>
      <div class="form-control form-control-check">
        <label>Set Reminder</label>
        <input type="checkbox" v-model="reminder" name="reminder" />
      </div>
  
      <input type="submit" value="Save Task" class="btn btn-block" />
    </form>
  </template>
  
  <script>
  export default {
    name: 'AddTask',
    data() {
      return {
        text: '',
        day: '',
        reminder: false,
      }
    },
    methods: {
        //Ka cia paduodame?????????????
        //passing our event object
      onSubmit(e) {
        //ka reiskia??????????????
        e.preventDefault()
        if (!this.text) {
          alert('Please add a task')
          return
        }
        //Pakuriam nauja task objekta
        const newTask = {
          //this id gets added by json-server
          //id: Math.floor(Math.random() * 100000),
          //whatever what is in the form because what we type in, gets binded to text variable inside data
          text: this.text, 
          day: this.day,
          reminder: this.reminder,
        }
        //perduodam task objekta i aukstesne klase (komponenta)
        this.$emit('add-task', newTask)
        this.text = ''
        this.day = ''
        this.reminder = false
      },
    },
  }
  </script>
  
  <style scoped>
  .add-form {
    margin-bottom: 40px;
  }
  .form-control {
    margin: 20px 0;
  }
  .form-control label {
    display: block;
  }
  .form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
  }
  .form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .form-control-check label {
    flex: 1;
  }
  .form-control-check input {
    flex: 2;
    height: 20px;
  }
  </style>