<template>
  <div>
    <h2>{{name}}</h2>
    <button @click="setName">Change Name</button>

    <h2>{{count}}</h2>
    <button @click="incrementCount">Increment Count</button>

    <h2>{{first}} {{last}}</h2>
    <button @click="changeHero">Change Hero</button>

  </div>
</template>

<script>
import {reactive, ref, toRefs} from "vue";

export default {
  name: "MethodsComponent",
  setup(){
    const count = ref(0)
    const state = reactive({
      first: 'BBB',
      last: 'CCC',
    })
    function incrementCount(){
      count.value++
    }

    function changeHero(){
      state.first = 'clark'
      state.last = 'kent'
    }
    return {
      count,
      incrementCount,
      ...toRefs(state),
      changeHero,
    }
  },
  data (){
    return {
      name: 'Nourrr',
    }
  },
  methods:{
    setName(){
      this.name = 'MMMMMMMM'
    }
  }
}
</script>

<style scoped>

</style>