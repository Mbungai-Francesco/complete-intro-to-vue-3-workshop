<script setup lang="ts">
// import { ref } from "vue";
import type { Char } from '../types/char.ts'

interface Props {
  char : Char
}
const { char } = defineProps<Props>()
const emit = defineEmits(['favourite'])
</script>

<template>
  <!-- <ul v-else-if="characters.length % 2 == 0"> -->
    <div>
      <p>Name: {{ char.name }} <span v-show="char.fav">⭐</span></p>
      <p>
        Elements: <span v-for="(ele, index) in char.elements" :key="index">{{ ele }}, </span>
      </p>
      <input type="button" value="Fav" @click="emit('favourite')" />
    </div>
</template>
