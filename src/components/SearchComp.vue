<template>
  <div>
    <input type="text" v-model="inputEmit" @keyup.enter ="$emit('emit1',inputEmit)">
  </div>
</template>

<script>
export default {
    name: "SearchComp",
    data () {
      return {
        inputEmit: '',
      }
    }
}
</script>

<style lang="scss" scoped>

</style>