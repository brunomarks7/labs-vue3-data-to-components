<template>
  <div class="hello2">
    <ul v-if="people.length">
      <li v-for="(people, index) in people" :key="index">
        <span>{{people}} <button @click="removeItem(index)">remove</button></span>
      </li>
    </ul>
    <h2 v-else>Star Wars People</h2>
  </div>
</template>

<script>
import { defineComponent } from "vue";
export default defineComponent ({
  name: 'ChildChild',
  props: {
    people: Array,
    removeItem: {
      type: Function,
      default: (index) => console.log(index)
    }
  }
})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello2 {
  background: black;
  color: white;
  padding: 20px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 0 15px;
  padding: 10px;
}
a {
  color: #42b983;
}
</style>
