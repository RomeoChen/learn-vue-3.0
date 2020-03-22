<template>
  <span>姓名: {{name}}</span><br/>
  <span>反转姓名: {{revertName}}</span><br/>
  <span>年龄: {{age}}</span><br/>
  <span>身高: {{currHeight}}</span><br/>
  <button @click="taller">长高1cm</button>
  <button @click="initHeight">还原身高</button>
</template>

<script>
import { reactive, ref, computed, watch } from 'vue'
export default {
  props: {
    name: String,
    age: Number,
    height: Number,
  },
  setup(props) {
    const currHeight = ref(props.height);
    const taller = () => {
      currHeight.value ++;
    }
    const initHeight = () => {
      currHeight.value = props.height;
    }

    const revertName = computed(() => {
      return props.name.split('').reverse().join('');
    })

    watch(
      () => currHeight.value,
      val => {
        console.log('watch', val)
        return val + 1;
      },
    )


    return {
      currHeight,
      taller,
      initHeight,
      revertName,
    }
  }
}
</script>

<style>

</style>