<template>
  <div class="main">

    <div class="header">
      <p class="date">{{ date }}</p>
      <h1>VueJs Tutorial ToDoList</h1>
      <p v-if="listeTache.length > 1">{{ listeTache.length }} tâches</p>
      <p v-if="listeTache.length <= 1">{{ listeTache.length }} tâche</p>
    </div>

    <NewTodo @newTask="addTask"></NewTodo>
    <div class="flex">
      <p @click="DeleteAll" class="button">Delete All</p>
      <p @click="DeleteCompleted" class="button">Delete Completed</p>
    </div>
    <div v-for="(item, index) in listeTache">
      <TodoList @complete="completed" @deleteTask="deleteOneTask" :title="item.name" :id="index"></TodoList>
    </div>

  </div>
</template>

<script>
import NewTodo from "@/components/NewTodo";
import TodoList from "@/components/TodoList";

export default {
  name: "ToDoCard",
  components: {
    NewTodo,
    TodoList
  },
  data() {
    return {
      listeTache: []
    }
  },
  computed: {
    date: function () {
      const now = new Date()
      const day = now.toLocaleString("default", {weekday: "long"})
      const dayNumber = now.getDay()
      const month = now.toLocaleString("default", {month: "long"})
      return `${day}  ${dayNumber}  ${month}`
    }
  },
  methods: {
    addTask(task) {
      this.listeTache.push({
        name: task,
        isDone: false,
      })
    },
    deleteOneTask(id) {
      this.listeTache.splice(id, 1)
    },
    DeleteAll() {
      this.listeTache = []
    },
    completed(id) {
      console.log(id)
      if (this.listeTache[id].isDone === true) {
        this.listeTache[id].isDone = false
      } else {
        this.listeTache[id].isDone = true
      }
    },
    DeleteCompleted() {
      for (var i = 0; i < this.listeTache.length; i++) {
        if (this.listeTache[i].isDone === true) {
          this.listeTache.splice(i, 1)
        }
      }
    },
  }
}
</script>

<style lang="scss" scoped>

.date {
  text-transform: capitalize;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}

.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */
{
  opacity: 0;
}

.button {
  padding: 5px 10px;
  background: orangered;
  color: white;
  width: 100px;
  text-align: center;
  border-radius: 10px;
  margin: 0px auto 30px;
}

.main {
  width: 70%;
  margin: auto;
  background: white;
  border-radius: 15px;
  padding-bottom: 20px;
}

.header {
  display: flex;
  justify-content: space-between;
  padding: 20px;
  border-bottom: 2px solid #00000020;

  h1, p {
    font-size: 1.3rem;
    font-weight: bold;
    font-family: Arial;
  }

  h1 {
    color: #00D1B3;
  }

  p {
    color: #636368;
  }
}
</style>