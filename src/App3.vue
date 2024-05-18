<template>

  <!-- <div>{{ 'value is: ' + counter }}</div>
  <div>{{ 'double value is: ' + doubleValue }}</div> -->

  <ASquare :num="counter" />
  <ASquare :num="doubleValue" />

  <!-- <button
    @click="console.log('click')"
    @mouseleave="console.log('mouseleave')"
  >click me!</button> -->
  <button @click="counter++">plus</button>
  <button @click="counter--">minus</button>

  <div class="container">
    <ASquare v-for="num in numbers" :num="num" />
  </div>
  <div class="container">
    <ASquare v-for="num in doubleNumbers" :num="num" />
  </div>

  <button @click="incrementAll">increment all</button>
  <button @click="addRandomNumber">add random number</button>

</template>

<script>
import ASquare from '@/components/ASquare.vue'
export default {
  name: 'App',
  data () {
    return {
      counter: 0,
      numbers: [28, 90, 1, 7, 25, 15]
    }
  },
  computed: {
    doubleValue () {
      return 2 * this.counter
    },
    doubleNumbers () {
      return this.numbers.map(num => 2 * num)
    }
  },
  methods: {
    incrementAll () {
      this.numbers = this.numbers.map(num => num + 1)
    },
    addRandomNumber () {
      const rnd = Math.floor(Math.random() * 100)
      this.numbers.push(rnd)
    }
  },
  components: {ASquare}

}

</script>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  margin: 1rem;
}
</style>