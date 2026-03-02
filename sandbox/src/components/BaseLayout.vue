<script setup lang="ts"></script>

<template>
  <div>
    <div class="wrapper">
      <aside class="sidebar">
        <slot name="sidebar"></slot>
      </aside>
      <main>
        <slot name="main"></slot>
      </main>
    </div>
    <footer>
      <slot name="foot"></slot>
    </footer>
  </div>
</template>

<style>
.sidebar {
  border: 2px solid red;
}
main {
  border: 2px solid green;
}
footer {
  border: 2px solid blue;
}
</style>
