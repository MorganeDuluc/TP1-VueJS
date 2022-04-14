<template>
  <div id="container">
    <ul v-for="(task, index) in tasksList" :key="index" id="container-list">
      <li id="list">
        <div id="infos">
          <p id="nameStyle">{{ task.nameTask }}</p>
          <p id="timeStyle">{{ task.timeTask}} heures estimées</p>
          <p id="workerStyle">{{ task.workerTask }}</p>
        </div>
        <div id="actions">
          <button class="button" v-on:click="deleteTask(index)">Supprimer</button>
          <button class="button" v-on:click="updateTask()">Modifier</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>

export default({
  name: "ToDoList",

  data() {
    return {
      name: '',
      time: '',
      worker: '',
    }
  },

  methods: {
    addNewTask: function() {
      this.tasksList.push({
        nameTask: this.name,
        timeTask: this.time,
        workerTask: this.worker
      })
    },

    deleteTask(index) {
      this.tasksList.splice(index, 1)
    },

    // updateTask: function () {
    //   this.tasksList.update({
    //     nameTask: this.name,
    //     timeTask: this.time,
    //     workerTask: this.worker
    //   })
    // }
  }
})
</script>

<style>
  #container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }

  #container-list {
    list-style-type:none;
    border: 1px solid #ff4200;
    width: 450px;
    height: 150px;
    display: flex;
    margin-top: 32px;
  }

  #list {
    display: grid;
    height: fit-content;
    grid-template-columns: repeat(2, 1fr);
  }

  #nameStyle {
    justify-content: start;
    display: flex;
    padding-top: 8px;
  }

  #timeStyle {
    font-style: italic;
    font-size: 12px;
    color: #707070;
    justify-content: start;
    display: flex;
  }

  #workerStyle {
    color: #ff4200;
    justify-content: start;
    display: flex;
  }
</style>