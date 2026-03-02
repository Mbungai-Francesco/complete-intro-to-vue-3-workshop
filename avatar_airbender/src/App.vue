<script lang="ts">
import VueCharacters from './components/VueCharacters.vue'
import FavouriteList from './components/FavouriteList.vue'


export default {
  components:{
    VueCharacters,
    FavouriteList
  },
  data: () => ({
    characters: [
      {
        id: '917c2904-1dab-451c-8f03-a1f0908d564d',
        name: 'Aang',
        fav: false,
        elements: new Set(['water', 'air', 'earth', 'fire']),
      },
      {
        id: 'd35a41e1-8148-4e8e-9dc8-7887d15bdea5',
        name: 'Zuko',
        fav: false,
        elements: new Set(['fire']),
      },
      {
        id: '3edf093d-52dd-479b-9977-28e4ede6523a',
        name: 'Toph',
        fav: false,
        elements: new Set(['earth']),
      },
      {
        id: '2b4e492f-2941-4b42-af30-4946a9c1ed42',
        name: 'Katara',
        fav: false,
        elements: new Set(['water']),
      },
    ],
    name: '',
    element: '',
    fav: false,
  }),
  computed: {
    elements() {
      return this.element.split(', ')
    },
    benderStatistics() {
      const eles = [
        { ele: 'Water', num: 0 },
        { ele: 'Air', num: 0 },
        { ele: 'Earth', num: 0 },
        { ele: 'Fire', num: 0 },
      ]
      eles.forEach((val) => {
        this.characters.forEach((char) => {
          if (char.elements.has(val.ele.toLowerCase())) val.num++
        })
      })
      return eles
    },
  },
  methods: {
    favBtn(pos : number) {
      console.log(pos)
      if(this.characters[pos])
      this.characters[pos].fav = !this.characters[pos].fav
    },
    createChar() {
      const ran = Math.ceil(Math.random() * 10000)
      const iD = this.name + ran
      const char = {
        id: iD,
        name: this.name,
        fav: false,
        elements: new Set(this.elements),
      }
      this.name = this.element = ''
      this.characters.push(char)
    },
  },
}
</script>

<template>
  <form action="">
    <label for="name"
      >Name:
      <input type="text" v-model="name" />
    </label>
    <label for="name"
      >Element:
      <input type="text" v-model="element" placeholder="water, air" />
    </label>
    <input type="submit" value="Create" @click.prevent="createChar" :disabled="!name || !element" />
  </form>

  <h2>Statistics</h2>
  <ul>
    <li v-for="(stats, index) in benderStatistics" :key="index">
      {{ stats.ele }} benders: {{ stats.num }}
    </li>
  </ul>

  <h2>Characters</h2>
   <p v-if="characters.length == 0">There are no characters</p>
   <ul v-else>
    <li v-for="(val, index) in characters" :key="val.id">
      <VueCharacters  :char="val" @favourite="favBtn(index)"/>
      
    </li>
  </ul>
  <!-- <p v-else>There are odd characters</p> -->

  <FavouriteList :chars="characters" />

  <p>
    <span v-for="(char, index) in characters" :key="index"
      >{{ char.name }}{{ index === characters.length - 1 ? '' : ', ' }}</span
    >
  </p>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>
