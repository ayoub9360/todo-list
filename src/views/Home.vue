<template>
  <main>
    <ToDoCard></ToDoCard>
  </main>
</template>

<script>
import ToDoCard from "@/components/ToDoCard";

export default {
  name: "Home",
  components: {
    ToDoCard,
  }
}
</script>

<style lang="scss" scoped>

main {
  min-height: 100vh;
  background: rgb(255, 217, 80);
  background: linear-gradient(101deg, rgba(255, 217, 80, 1) 0%, rgba(255, 193, 55, 1) 100%);
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>