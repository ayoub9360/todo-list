<template>
  <div class="main">
    <input type="text" placeholder="Nouvelle tâche..." v-model="inputValue">
    <!--    <button type="submit" @click="submitTask">ADD</button>-->
    <a class="button" v-on:click="submitTask">ADD</a>

  </div>
</template>

<script>
export default {
  name: "NewTodo",
  data() {
    return {
      inputValue: ""
    }
  },
  methods: {
    submitTask() {
      if (this.task !== '') {
        this.$emit('newTask', this.inputValue)
      }
      this.inputValue = ''
    }
  }
}
</script>

<style lang="scss" scoped>
.main {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 30px 0;
}

input {
  padding: 10px 40px;
  border: none;
  border-bottom: solid 2px #00D1B3;
  margin: 0 20px;
}

.button {
  background: #49C774;
  padding: 20px 15px;
  border-radius: 50%;
  border: none;
  color: white;
  cursor: pointer;
}
</style>