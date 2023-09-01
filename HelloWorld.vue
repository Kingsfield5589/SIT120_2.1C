<template>
 <div class="todo-app">
    <h1>Todo App</h1>
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Enter a new task">
    <ul>
        <li v-for="(task, index) in tasks" :key="index">
            <input type="checkbox" v-model="task.completed">
            <span :class="{ completed: task.completed }">{{ task.text }}</span>
            <button @click="removeTask(index)">Remove</button>
        </li>
    </ul>
 </div>
</template>
 
<script>
export default {
 data() {
 return {
 newTask: '',
 tasks: []
 };
 },
 methods: {
 addTask() {
 if (this.newTask.trim() !== '') {
 this.tasks.push({
 text: this.newTask,
 completed: false
 });
 this.newTask = '';
 }
 },
 removeTask(index) {
 this.tasks.splice(index, 1);
 }
 }
};
</script>
 
<style scoped>
.todo-app {
 max-width: 400px;
 margin: 0 auto;
 text-align: center;
 font-family: Arial, sans-serif;
 color: #000000;
}
 
ul {
 list-style: none;
 padding: 0;
}
 
li {
 margin: 0 auto;
 align-items: center;
 margin: 10px 0;
}
 
.completed {
 text-decoration: line-through;
 color: #888;
}
 
button {
 margin-left: 10px;
 padding: 5px 10px;
 background-color: #f44336;
 border: none;
 color: white;
 cursor: pointer;
}

</style>