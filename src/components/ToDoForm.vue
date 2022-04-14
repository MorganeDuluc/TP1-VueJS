<template>
<div>
  <!-- <form @submit="onSubmit" id="form">
    <div class="boxInput">
      <label for="title">Title</label>
      <input required type="text" title="title" id="title" name="title" v-model="title">
    </div>

    <div class="boxInput">
      <label for="title">Heure estimée</label>
      <input required type="number" title="hours" id="hours" name="hours" v-model="hours">
    </div>

    <select v-model="workers" name="people" required>
      <option disabled value="">Choisissez</option>
      <option>Gui</option>
      <option>Vinx</option>
      <option>Julie</option>
    </select>
    <span>Sélectionné : {{ workers }}</span>

    <button type="submit">Valider</button>
  </form> -->

  <div id="todo-list-example">
    <form v-on:submit.prevent="addNewTodo" id="form">
      <div class="boxInput">
        <label for="new-name-task">Ajouter une tâche</label>
        <input
          v-model="nameTask"
          id="new-name-task"
          placeholder="Ex. Faire le webdesign"
          required
        >
      </div>
      <div class="boxInput">
        <label for="new-time-task">Heure estimée</label>
        <input
          type="number"
          v-model="hours"
          id="new-time-task"
          placeholder="Ex. 2 heures"
          required
        >
      </div>
      <div>
        <select v-model="workers" name="people" required>
          <option disabled value="">Choisissez</option>
          <option>Gui</option>
          <option>Vinx</option>
          <option>Julie</option>
        </select>
      </div>

      <button>Add</button>
    </form>
    <ul>
      <li
        is="task-title"
        v-for="(todo, index) in todos"
        v-bind:key="todo.id"
        v-bind:title="todo.title"
        v-on:remove="todos.splice(index, 1)"
      />
      <li
        is="task-hour"
        v-for="(todo, index) in todos"
        v-bind:key="todo.id"
        v-bind:hour="todo.hour"
        v-on:remove="todos.splice(index, 1)"
      />
      <li
        is="task-worker"
        v-for="(todo, index) in todos"
        v-bind:key="todo.id"
        v-bind:worker="todo.worker"
        v-on:remove="todos.splice(index, 1)"
      />
    </ul>
  </div>
</div>
</template>

<script>

// export default {
//   name: "ToDoForm",

//   data() {
//     return {
//       workers: '',
//       hours: '',
//       title: '',
//       list: [],
//     }
//   },

//   methods:{
//     onSubmit: function(e) {
//       console.log("=====================")
//       console.log(e)
//       console.log(e.target)
//       e.preventDefault()
//     },

//     displayList: function() {
//       this.list = [];

//       if (this.title && this.hours && this.workers) {
//         return (
//           t
//         )
//       }
//     }
//   }
// }

export default({
  name: "ToDoForm",
  el: '#todo-list-example',

  // template: '\
  //   <li>\
  //     {{ title }}\
  //     <button v-on:click="$emit(\'remove\')">Supprimer</button>\
  //   </li>\
  // ',
  // props: ['title'],

  data() {
    return {
      nameTask: '',
      todos: [
        {
          id: 1,
          title: 'Faire la vaisselle',
          hour: '',
          worker: 'Gui',
        },
      ],
      nextTodoId: 2
    }
  },

  methods: {
    addNewTodo: function () {
      this.todos.push({
        id: this.nextTodoId++,
        title: this.nameTask
      })
      this.nameTask = ''
    }
  }
})
</script>

<style>
  #form {
    background-color: #bbbbbb;
    height: 80px;
    border-radius: 24px;
    justify-content: space-between;
    align-items: center;
    display: flex;
    padding: 0 16px 0 16px;
  }

  .boxInput {
    flex-direction: column;
    display: flex;
  }

  input {
  padding: 4px; border-radius: 16px; border: none; height: 20px; } label {
    justify-content: left;
    display: flex;
    font-size: 12px;
    margin-bottom: 4px;
  }

  button {
    padding: 8px;
    border-radius: 16px;
    background-color:cadetblue;
    color:white;
    border: none;
    height: 40px;
    width: 100px;
  }

  select {
    padding: 4px;
    border-radius: 16px;
    border: none;
    height: 20px;
  }
</style>