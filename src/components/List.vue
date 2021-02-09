<template>
  <div class="list">
    <ul>
      <ListItem :todo=todo v-for="todo in todos" v-bind:key="todo.title" />
    </ul>
  </div>
</template>

<script>
import ListItem from './ListItem.vue'
import axios from "axios";


export default {
  name: 'List',
  components: {
    ListItem
  },
  data () {
    return {
      todos: []
    };
  },
  mounted () {
    axios
      .get('https://jsonplaceholder.typicode.com/todos')
      .then(response => (this.todos = response.data))
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
