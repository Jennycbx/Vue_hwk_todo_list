<template>
  <div id="app">
    <ul>
      <li v-for="(task, index) in tasks" :key="index"
      v-bind:class="task.priority ? 'high-priority' : 'low-priority' ">
        <span>{{task.name}}</span>
      </li>
    </ul>

    <form v-on:submit.prevent="saveNewTask">
      <label for="new-task">Add a new task</label>
      <input type="text" id="new-task" v-model="newTask">
      <input type="radio" id="high-priority" name="priority" value="high-priority">
      <label for="high-priority">High Priority</label>
      <input type="radio" id="low-priority" name="priority" value="low-priority">
      <label for="low-priority">Low Priority</label>
      <input type="submit" value="Save new task">
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        {name: "Buy shopping", priority: true},
        {name: "Clean bathroom", priority: false},
        {name: "Car's MOT", priority: true},
      ],
      newTask: ""
    }
  },
  methods: {
    saveNewTask: function() {
      this.tasks.push({
        name: this.newTask})
      this.newTask = "";
    }  
  }
}
</script>

<style>
#app {
  width: 60%;
  margin: 0 auto;
  font-family: 'Lato', sans-serif;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

li {
  margin: 20px 0;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}

li span {
  padding: 8px;
}

li.low-priority {
  border: 2px solid #1a681e;
  color: #1a681e;
}

li.high-priority {
  border: 2px solid #f2360c;
  color: #f2360c;
}

li button {
  background: #f2360c;
  color: #fff;
  border: none;
  padding: 10px;
  cursor: pointer;
}
input[type="text"] {
  padding: 10px;
  width: 50%;
  margin:5px;
}

button, input[type="submit"]{
  padding: 10px;
  background: #000;
  color: #fff;
  cursor: pointer;
  border: 1px solid #000;
}

</style>
