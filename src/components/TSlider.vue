<template>
  <div class="container">
    <div class="main">
      <!-- <button @click="changeIndex('minus')" :disabled="!displayBtnLeft">
        back</button> -->
      <TButton label="back" @clicked="changeIndex('minus')" :disabled="!displayBtnLeft" />
      <div>{{ content[indexToDisplay] }}</div>

      <!-- <button @click="changeIndex('plus')" :disabled="!displayBtnRight">
        forward
      </button> -->
      <TButton label="forward" @clicked="changeIndex('plus')" :disabled="!displayBtnRight" />

    </div>
    <div class="below">{{ labelBelow }}</div>
  </div>
</template>

<script>

import TButton from '@/components/TButton.vue'

  export default {
    name: 'TSlider',
    props: {
      content: Array
    },
    data () {
      return {
        indexToDisplay: 0,
        disableLeft: false,
        disableRight: false
      }
    },
    computed: {
      labelBelow () {
        return `${this.indexToDisplay + 1}/${this.content.length}`
      },
      displayBtnRight () {
        return this.indexToDisplay < this.content.length - 1
      },
      displayBtnLeft () {
        return this.indexToDisplay > 0
      }
    },
    methods: {
      increment () {
        // console.log(event)
        this.indexToDisplay = this.indexToDisplay === this.content.length - 1 ? 0 : this.indexToDisplay + 1
        // if (this.indexToDisplay === this.content.length - 1) {
        //   this.disableRight = true
        // } else {
        //   this.disableRight = false
        // }
      },
      decrement () {
        this.indexToDisplay = this.indexToDisplay === 0 ? this.content.length - 1 : this.indexToDisplay - 1
      },
      changeIndex (par) {
        // par === 'plus' ? this.increment() : this.decrement()
        this[par ==='plus' ? 'increment' : 'decrement']()
      }
    },
    components: {TButton}
  }

</script>

<style scoped>
.container {
  width: 300px;
}

.main {
  display: flex;
  justify-content: space-between;
  gap: .5rem;
}
</style>