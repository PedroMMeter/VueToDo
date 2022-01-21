<template>
  <div class="container">
    <form class="createWrapper" @submit.prevent="addTodo">
      <input v-model="todotext" />
      <div>
        <button 
        type="submit" 
        class="form-button" 
        :disabled='todotext === ""'
        :class="{disabledButton : todotext === ''}"
        >
          Adicionar Tarefa
        </button>
      </div>
    </form>
    <div class="todoWrapper">
      <ol class="todoList">
        <li class="itemTile" v-for="todo in todos" :key="todo.id" :class="{doneTask : todo.done}">
          <p style="font-weight: bold; font-size: 1.5rem;">{{ todo.todotext }}</p>
          <input class="check-input" type="checkbox" v-model='todo.done'>
          <button class="form-button" @click='removeThisTodo(todo)'>Remover</button>
        </li>
      </ol>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDo",
  data() {
    return {
      todos: [],
      id: 1,
      todotext: '',
      complete: false,
    };
  },
  methods: {
    reset(){
      this.id++,
      this.todotext = '',
      this.complete = false
    },
    addTodo() {
      let todo = {
        id: this.id,
        todotext: this.todotext,
        complete: this.complete,
      }
      this.todos.push(todo);
      this.reset()
    },
    removeThisTodo(todo) {
        const indx = this.todos.indexOf(todo)
        this.todos.splice(indx, 1);
    }
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;

  padding: 2rem;
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
  
  border-radius: 0.46rem;

  background: #232433;
}
.createWrapper {
  background: #e2e7d7;
  min-height: 4rem;
  max-height: fit-content;
  border-radius: 0.4rem 0.4rem 0 0;
}
.createWrapper input {
  padding: 0.2rem;
  margin: 0.6rem 0 auto auto;
  height: 1.5rem;
  
  border: 1px solid #ccc;
  border-radius: 0.2rem;
  
  background-color: rgba(255, 255, 255, 0.9);
  font-family: "Poppins", sans-serif;
}
.form-button {
  margin: 0.5rem;
  padding: 0.3rem;
  height: 2rem;
  
  border: none;
  border-radius: 0.2rem;

  color: #fff;
  background: #565a96;

  
  font-family: "Poppins", sans-serif;
  font-size: 0.85rem;
  cursor: pointer;
}
.disabledButton{
  background: #565a969c ;
  color: rgba(255, 250, 250, 0.671);
  cursor: default;
}
.todoList {
  min-height: 16rem;
  max-height: fit-content;
  
  margin: 0.6rem auto;
  padding: 1rem 0;

  list-style: none;
  background: #e2e7d7;
  
  border-radius: 0 0 0.4rem 0.4rem;
}
.itemTile {
  width: 90%;
  margin: 1rem auto;
  
  background: #66b7bd;
}
.doneTask{
  text-decoration: line-through;
}
.check-input{
  height: 1rem;
  width: 1rem;

  cursor: pointer;
}

</style>