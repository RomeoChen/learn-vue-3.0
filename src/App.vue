<template>
  <img src="./logo.png">
  <h1>Hello Vue 3!</h1>
  <button @click="inc">Clicked {{ count }} times.</button>
  <button @click="inc">Clicked {{ count }} times.</button><br/>
  <User :name="name" :age="age" :height="height"> </User>
</template>

<script>
import { ref, reactive, toRefs } from 'vue'
import User from './components/User.vue';

export default {
  components: {
    User,
  },
  setup() {
    const count = ref(0)
    const inc = () => {
      count.value++
    }

    const User = reactive({
      name: 'romeo',
      age: 24,
      height: 175
    })

    return {
      count,
      inc,
      ...toRefs(User),
    }
  }
}
</script>

<style scoped>
img {
  width: 200px;
}
h1 {
  font-family: Arial, Helvetica, sans-serif;
}
</style>
