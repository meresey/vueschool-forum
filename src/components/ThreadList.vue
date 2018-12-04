<template>
  <div class="container">
    <h2 class="list-threads">Threads</h2>
    <ThreadListItem v-for="thread in threads" :key="thread['.key']" :thread="thread"/>
  </div>
</template>

<script>
import ThreadListItem from "./ThreadListItem";
export default {
  components: {
    ThreadListItem
  },
  props: {
    threads: {
      required: true,
      type: Array
    }
  }
};
</script>

<style scoped>
.container {
width: 800px;
    background-color: white;
}
.list-threads {
  background-color: #2c3e50;
  color: white;
  border-radius: 0 0 0 20px;
  padding-left: 5px;
  font-weight: 400;
  margin: 0;
}
</style>
