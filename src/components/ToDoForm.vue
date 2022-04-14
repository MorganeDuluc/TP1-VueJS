<template>
  <div>
    <form v-on:submit.prevent="addNewTask" id="form">
      <div class="boxInput">
        <label for="name">Ajouter une tâche</label>
        <input
          v-model="name"
          id="name"
          required
        >
      </div>
      <div class="boxInput">
        <label for="time">Heure estimée</label>
        <input
          type="number"
          v-model="time"
          id="time"
          required
        >
      </div>
      <div class="boxInput">
        <label for="worker">Responsable</label>
        <select
          v-model="worker"
          id="worker"
          name="worker"
          required>
          <option disabled value=""/>
          <option>Gui {{option}}</option>
          <option>Vinx {{option}}</option>
          <option>Julie {{option}}</option>
        </select>
      </div>

      <button type="submit">Ajouter</button>
    </form>

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
  </div>
</template>

<script>



export default({
  name: "ToDoForm",

  props: {
    option: String,
  },

  data() {
    return {
      name: '',
      time: '',
      worker: '',
      tasksList: [
        { nameTask: 'Construction des wirefram', timeTask: '2', workerTask: 'Gui', },
        { nameTask: 'Charte graphique', timeTask: '2', workerTask: 'Vinx', },
      ],
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
  #title {
    color: white;
  }

  #form {
    background-color: #dbdbdb;
    height: 80px;
    border-radius: 24px;
    justify-content: space-around;
    align-items: center;
    display: flex;
    padding: 32px 0 32px 0;
  }

  label {
    justify-content: left;
    display: flex;
    font-size: 12px;
    margin-bottom: 8px;
    color: #707070;
  }

  input {
    padding: 8px;
    /* border: 1px solid #FF4200; */
    border-radius: 8px;
    border: none;
    height: 20px;
    width: 200px;
    background-color: white;
  }

  select {
    padding: 8px;
    /* border: 1px solid #FF4200; */
    border-radius: 8px;
    border: none;
    width: 200px;
    height: 37px;
    background-color: white;
    color: #707070;
  }

  button {
    padding: 8px;
    /* border: 1px solid #ffffff; */
    border: none;
    border-radius: 50px;
    background-color: #1e2626;
    color:white;
    height: 40px;
    width: 120px;
    margin-top: 24px;
    cursor: pointer;
  }

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