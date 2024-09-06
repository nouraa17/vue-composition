<template>
  <div>
    <h2>Options - {{o_firstName}}</h2>

    <h2>Composition - {{c_firstName}}</h2>
    <h2>Composition - {{greet}}</h2>

    <h2>Composition - {{c_firstName}} {{c_lastName}} {{c_heroName}}</h2>
    <h2>Composition - {{greetHero}}</h2>

    <h2>Composition - {{ state.firstName }} {{ state.lastName }} {{ state.heroName }}</h2>
    <h2>Composition - {{reactiveGreetHero}}</h2>

  </div>
</template>

<script>
import {ref, reactive} from "vue";

export default {
  name: "DataComponent",
  setup(){
    const c_firstName = ref('a')
    const c_lastName = ref('b')
    const c_heroName = ref('c')
    console.log('c_firstName => ',c_firstName)
    const greet = `Hello ${c_firstName.value}`;
    const greetHero = `Hello ${c_firstName.value} ${c_lastName.value} a.k.a ${c_heroName.value}`;
    const state = reactive({
      firstName:'N',
      lastName:'M',
      heroName:'S',
    })
    const reactiveGreetHero = `Hello ${state.firstName} ${state.lastName} ${state.heroName}`
    return {
      c_firstName :c_firstName,
      greet,
      c_lastName,
      c_heroName,
      greetHero,
      state,
      reactiveGreetHero
    }


  },
  data(){
    return{
      o_firstName:'Nourhan',
      o_lastName:'Muhammad',
      o_heroName:'Super woman',
    }
  }
}
</script>

<style scoped>

</style>