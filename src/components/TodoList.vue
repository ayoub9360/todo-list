<template>
  <div class="main">
    <input @click="taskComplete(id)" type="checkbox" v-model="checked">
    <p :class="{ checked: checked }">{{ title }}</p>
    <button @click="deleteTask(id)">Delete</button>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: {
    title: String,
    id: Number,
  },
  data() {
    return {
      checked: null,
    }
  },
  methods: {
    deleteTask(id) {
      this.$emit('deleteTask', id)
    },
    taskComplete(id) {
      this.$emit('complete', id)
    }
  }
}
</script>

<style scoped>
.checked {
  text-decoration: line-through;
}

.main {
  display: flex;
  justify-content: space-between;
}

input {
  border-radius: 50%;
}

button {
  height: 20px;
  padding: 0 10px;
  background: red;
  border: none;
  border-radius: 10px;
  color: white;
}
</style>