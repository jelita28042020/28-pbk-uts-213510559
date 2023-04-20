<template>
  <div class="todo-list">
    <h1>Aplikasi Data Absensi</h1>
    <form @submit.prevent="addTodo">
      <input type="text" v-model="newTodo" placeholder="Input Data..." />
      <input type="datetime-local" v-model="newDate" />
      <button type="submit" class="tambahkan">Tambahkan</button>
    </form>
    <h2>List Item</h2>
    <div class="tengah">
      <ul>
        <li v-for="(todo, index) in todos" :key="index">
          <input type="checkbox" v-model="todo.done" />
          <span :class="{ 'done': todo.done }">{{ todo.text }}</span>
          <span>{{ todo.date }}</span>
          <button @click="removeTodo(index)">Remove</button>
        </li>
      </ul>
      <button @click="removeAllTodos">Remove All</button>
    </div>
    <footer>
      <p>&copy;Jelita Lestari</p>
    </footer>
  </div>
</template>


<script>
export default {
  data() {
    return {
      newTodo: '',
      newDate: '',
      todos: []
    }
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim().length === 0) {
        return
      }
      this.todos.push({
        text: this.newTodo,
        done: false,
        date: this.newDate ? new Date(this.newDate).toLocaleString() : new Date().toLocaleString()
      })
      this.newTodo = ''
      this.newDate = ''
    },
    removeTodo(index) {
      this.todos.splice(index, 1)
    },
    removeAllTodos() {
      this.todos = []
    }
  }
}
</script>


<style>
.todo-list {
  font-family: sans-serif;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}
body{
background-image: url(https://img.freepik.com/free-vector/hand-drawn-minimal-background_23-2149017009.jpg?w=1380&t=st=1681991783~exp=1681992383~hmac=fc4f381d824e1e26f69bffc1e916d1e9a3f2161210b387ba67a3465641de6d0e);
background-size: cover;
background-repeat: no-repeat;
background-position: center;
}
.todo-list h1 {
  font-size: 36px;
  margin-bottom: 20px;
  text-align: center;
}

.todo-list form {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

.todo-list input[type="text"] {
  flex: 1;
  font-size: 18px;
  padding: 10px;
  border: 2px solid #ccc;
  border-radius: 5px;
}

.todo-list input[type="datetime-local"] {
  width: 180px;
  font-size: 18px;
  padding: 10px;
  border: 2px solid #ccc;
  border-radius: 5px;
}

.todo-list button {
  font-size: 18px;
  padding: 10px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.todo-list button.tambahkan {
  margin-left: 10px;
}

.todo-list h2 {
  font-size: 24px;
  margin-bottom: 10px;
}

.todo-list ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.todo-list li {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.todo-list li span.date {
  font-size: 16px;
  color: #666;
}

.todo-list button.remove {
  background-color: #f44336;
}

.todo-list button.remove:hover {
  background-color: #da190b;
}

.todo-list button.remove:active {
  background-color: #da190b;
}
.done {
  text-decoration: line-through;
}
</style>