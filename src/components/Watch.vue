<template>
  <div>
    <!-- Options API -->
    <input type="text" placeholder="Name" v-model="name" />
    <hr>
    <!-- Composition API -->
    <input type="text" placeholder="First Name" v-model="firstName" /><br>
    <input type="text" placeholder="Last Name" v-model="lastName" /><br>

    <hr>

    <input type="text" placeholder="Reactive First Name" v-model="fname" /><br>
    <input type="text" placeholder="Reactive Last Name" v-model="lname" /><br>
    <input type="text" placeholder="Reactive Hero Name" v-model="options.heroName" /><br>
  </div>
</template>

<script>
import {ref,watch, reactive, toRefs} from "vue";
import _ from 'lodash';
export default {
  name: "WatchComponent",
  setup(){
    const state = reactive({
      fname: '',
      lname: '',
      options: {
        heroName: '',
      },
    })


    watch(()=> _.cloneDeep(state.options) , function (newValue,oldValue){
      console.log('F name Old value ', oldValue)
      console.log('F name New value ', newValue)
    },
        {
          deep: true
        })


    watch(//state -> instead we pass copy
        () => {
          return{
            ...state
          }
        }
        , function (newValue, oldValue){
      console.log('F name Old value ', oldValue.fname)
      console.log('F name New value ', newValue.fname)
      console.log('L name Old value ', oldValue.lname)
      console.log('L name New value ', newValue.lname)
    })

    const firstName = ref('')
    const lastName = ref('MU')

    watch([firstName,lastName], (newValues, oldValues) => {
      console.log('First name Old value ', oldValues[0])
      console.log('First name New value ', newValues[0])
      console.log('last name Old value ', oldValues[1])
      console.log('last name New value ', newValues[1])
    },
        {
      immediate: true
    })

    return {
      firstName,
      lastName,
      ...toRefs(state)
    }
  },
  data() {
    return {
      name: '',
    }
  },
    watch:{
      name(newValue, oldValue){
      console.log('Old value ', oldValue)
      console.log('New value ', newValue)
      },
    },
}
</script>


<style scoped>

</style>
