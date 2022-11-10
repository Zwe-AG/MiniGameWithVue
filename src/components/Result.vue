<template>
  <p>Result is {{ score }}</p>
  <div v-if="score<250">
    <p>You are so fast</p>
  </div>
  <div v-else-if="score>250 && score<500">
    <p>You are normal</p>
  </div>
  <div v-else>
    <p>You are very slow Try Again!!!</p>
  </div>
</template>

<script>
export default {
props:['score']
}
</script>

<style>

</style>