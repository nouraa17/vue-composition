<template>
  <div>
<!--    <h2>{{state.firstName}} {{state.lastName}}</h2>-->

    <h2>{{firstName}} {{lastName}}</h2>
    <h2>{{fname}} {{lname}}</h2>
  </div>
</template>

<script>
import {reactive, toRefs} from "vue";

export default {
  name: "DemoTwo",
  setup(){
    const state = reactive({
      firstName: 'Nour',
      lastName: 'Muhammad',
    })
    setTimeout(()=>{
      state.firstName = 'N'
      state.lastName = 'M'
    },2000)
    return toRefs(state)
    // {
    //   firstName:state.firstName,
    //   lastName:state.lastName,
    // }
  },
  data(){
    return{
      fname: 'abc',
      lname:'def'
    }
  }
}
</script>

<style scoped>

</style>