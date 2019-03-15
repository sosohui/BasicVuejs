<template>
  <div id="app">
    <div class="container">
      <div class="col-md-6 offset-md-3">
        <h1 class="title text-center">Todo 어플리케이션</h1>
        <b-form-input type="text" class="form-comtrol mb-4" v-model="userInput" @keyup.enter="addNewTodo" placeholder="new Todo"/>
        <div class="list-group mb-4">
          <template v-for="todo in activeTodoList">
            <todo
              :label="todo.label"
              @componentClick="toggleTodoState(todo)"
            />
          </template>
        </div>
        <div class="text-right">
          <b-button type="button" variant="outline-primary" class="btn btn-sm mx-1" @click="chageCurrentState('active')">할 일</b-button>
          <b-button type="button" variant="outline-primary" class="btn btn-sm mx-1" @click="chageCurrentState('done')">완료</b-button>
          <b-button type="button" variant="outline-primary" class="btn btn-sm mx-1" @click="chageCurrentState('all')">전체</b-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from './components/Todo'

export default {
  name: 'app',
  data () {
    return {
      userInput: '',
      todoList: [],
      currentState: 'active'
    }
  },
  computed: {
    activeTodoList() {
      return this.todoList.filter(todo => this.currentState ==='all' || todo.state === this.currentState)
    }
  },
  methods: {
    chageCurrentState(state) {
      this.currentState = state;
    },
    addNewTodo() {
      this.todoList.push({
        label: this.userInput,
        state: 'active'
      })
      this.userInput = '';
    },
    toggleTodoState(todo){
      todo.state = todo.state === 'active' ? 'done' : 'active'
    }
  },
  components: {
    Todo
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
