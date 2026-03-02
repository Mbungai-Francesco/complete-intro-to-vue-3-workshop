<script setup lang="ts">
import type { Char } from '@/types/char';

interface Props {
  chars: Char[]
}

const { chars } = defineProps<Props>()
</script>

<template>
  <h2>Favorites Characters</h2>
  <ul>
    <li v-for="val in chars" v-show="val.fav" :key="val.id">
      <p>{{ val.name }} <span v-show="val.fav">⭐</span></p>
    </li>
  </ul>
</template>
