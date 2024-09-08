<template>
  <div>
    <input type="text" placeholder="First Name" v-model="firstName">
    <input type="text" placeholder="Last Name" v-model="lastName">
    <hr>
    <PersonGreeting :firstName="firstName" :lastName="lastName" @callHeroes="callHeroes"></PersonGreeting>
  </div>
</template>

<script>
import {ref} from "vue";
import PersonGreeting from "@/components/PersonGreeting.vue";

export default {
  name: "PersonComponent",
  components:{
    PersonGreeting
  },
  setup (){
    const firstName = ref('')
    const lastName = ref('')

    function callHeroes(hero){
      alert(`Calling ${hero}`)
    }
    return{
      firstName,
      lastName,
      callHeroes,
    }
  }
}
</script>


<style scoped>

</style>