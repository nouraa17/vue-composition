<template>
  <div>
    <h2>Hello {{firstName}} {{lastName}}</h2>  <!-- without computed -->
    <h2>Hello {{fullName}}</h2> <!-- with computed -->
    <hr>
    <button @click="sendEvent">Call Heroes</button>
  </div>
</template>

<script>
import {computed} from "vue";
export default {
  name: "PersonGreeting",
  setup(props, context){
    console.log(context)
    const fullName = computed(()=> {
      return `${props.firstName} ${props.lastName}`
    })

    function sendEvent(){
      context.emit('callHeroes', fullName.value)
    }

    return {
      fullName,
      sendEvent,
    }
  },
  props: ['firstName','lastName'],
  emits : ['callHeroes'],
  // computed : {
  //   fullName(){
  //     return `${this.firstName} ${this.lastName}`
  //   }
  // }
}
</script>


<style scoped>

</style>