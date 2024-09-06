<template>
  <div>
    <!--  options api  -->
    <input type="text" placeholder="First Name" v-model="fName" /><br>
    <input type="text" placeholder="Last Name" v-model="lName" /><br>

    <hr>

    <!--  composition api  -->
    <input type="text" placeholder="Hero Name" v-model="heroName" /><br>
    <input type="text" placeholder="First Name" v-model="firstName" /><br>
    <input type="text" placeholder="Last Name" v-model="lastName" /><br>
  </div>
</template>

<script>
import {reactive, ref, toRefs} from "vue";
export default {
  name: "VModel",
  setup(){
    const heroName = ref('')
    const state = reactive({
      firstName: '',
      lastName: '',
    })
    return {
      heroName,
      ...toRefs(state)
    }
  },
  data (){
    return{
      fName : '',
      lName : '',
    }
  }
}
</script>

<style scoped>

</style>