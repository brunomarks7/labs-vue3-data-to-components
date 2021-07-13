<template>
  <img alt="Vue logo" src="./assets/star-wars.svg" width="350">
  <HelloWorld :people="people"/>
  <br />
  <button @click="loadpeople">{{loading ? 'Loading' : 'Load People'}}</button>
</template>

<script>
import {defineComponent, ref} from "vue"
import HelloWorld from './components/HelloWorld.vue'


export default defineComponent ({
  name: 'App',
  components: {
    HelloWorld
  },
  setup(){
    let people = ref([]);
    let loading = ref(false);

    const loadpeople = () => {
      if(loading.value) return false;
      loading.value = true;
      fetch("https://swapi.dev/api/people")
        .then(res => res.json())
        .then(res => {
          const names = res?.results.map(v => v.name)
          people.value = [...people.value, ...names]
          loading.value = false;
        })
    }

    return {
      people,
      loadpeople,
      loading
    }
  }
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
