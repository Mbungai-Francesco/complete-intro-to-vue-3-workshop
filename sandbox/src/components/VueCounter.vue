<script lang=ts>

export default{
  data() {
    return {
      count: 0,
      addBy: 1,
      counter: 'Counter Standard',
    }
  },
  computed: {
    displayTitle() {
      if (this.count > 20) return 'Counter Standard - Very long '
      else return 'Counter Standard'
    },
    optimizedAddBy() {
      return this.displayTitle.length * this.addBy
    },
  },
  methods: {
    incrementCount(num : number, event: PointerEvent) {
      console.log(num);
      console.log(event);

      this.count += this.optimizedAddBy
    },
    handleIncrement(e : any) {
      this.addBy = e.target ?  Number(e.target.value) : 0
    },
  },
}

</script>

<template>
  <h1>{{ counter }}</h1>
  <p>{{ count }}</p>
  <input type="button" value="Count" @click="incrementCount(5, $event)" />
  <h1>{{ addBy }}</h1>
  <p>{{ optimizedAddBy }}</p>
  <div>
    <label for="addBy">Increment by:</label>
    <input type="number" v-model="addBy" />
  </div>

  <hr />
</template>

<style scoped></style>