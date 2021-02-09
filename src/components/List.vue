<template>
  <div class="list">
    <ul>
      <p>Winner: User {{ highestScore.userId }}</p>
      <p>Score: {{ highestScore.score }}</p>
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
  },
  computed: {
    highestScore() {
      let bestUser = {userId: null, score: 0}
      let currentUser = {userId: null, score: 0};
      this.todos.map((todo) => {
        if (currentUser.userId != todo.userId) {
          currentUser.userId = todo.userId
          currentUser.score = 0;
        }

        if (todo.completed) {
          currentUser.score++
        }

        if (currentUser.score > bestUser.score) {
          bestUser = currentUser;
        }
      })

      return bestUser;
    }
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
