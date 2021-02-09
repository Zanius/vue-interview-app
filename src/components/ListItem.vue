<template>
  <li>
    <p>title: {{todo.title}}</p>
    <p>completed: {{todo.completed}}</p>
  </li>
</template>

<script>


export default {
  name: 'ListItem',
  props: {
    todo: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
