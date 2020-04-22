<template lang="html">
  <div>
    <h3>{{character.name}}</h3>
    <p>{{character.species}}</p>
    <p>{{character.status}}</p>
  </div>
</template>

<script>
export default {
  name: 'character-detail',
  props: ['character']
}
</script>

<style lang="css" scoped>
</style>
