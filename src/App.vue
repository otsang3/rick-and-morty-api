<template lang="html">
  <div class="">
    <label for="character list">Select a Character</label>
    <select id="character list" v-model="selectedCharacter">
      <option v-for="character in characters">{{character.name}}</option>

    </select>
    <characters-list :characters="characters"></characters-list>
    <character-detail v-if="selectedCharacter" :character="selectedCharacter"></character-detail>
  </div>
</template>

<script>
import CharactersList from './components/CharactersList.vue';
import {eventBus} from './main.js';
import CharacterDetail from './components/CharacterDetail.vue';

export default {
  name: 'app',
  data(){
    return {
      characters: [],
      selectedCharacter: null
    }

  },
  mounted(){
    fetch('https://rickandmortyapi.com/api/character/')
    .then(response => response.json())
    .then(data => this.characters = data.results)

    eventBus.$on('characterSelected', (character) => {
      this.selectedCharacter = character;
    })
  },
  components: {
    'characters-list': CharactersList,
    'character-detail': CharacterDetail
  }
}
</script>

<style lang="css" scoped>
</style>
