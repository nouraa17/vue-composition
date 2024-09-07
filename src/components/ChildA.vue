<template>
  <h2>Child Component A</h2>
  <ChildB />
</template>

<script>
import ChildB from "@/components/ChildB.vue";
export default {
  name: 'ChildA',
  components: {
    ChildB,
  },
}
</script>

<style scoped>
</style>