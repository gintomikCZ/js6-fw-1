<template>
  <!-- pokud nejsou items - msg - no items to display -->
  <p v-if="noItems">there are no items to display</p>

  <!-- pokud je jen jedna položka, tak vypíšeme - the only item is: .... -->

  <p v-else-if="oneItem">{{  'the only item is: ' + items[0] }}</p>

  <!-- jinak kreslíme ulko -->
  <ul v-else>
    <!-- <li>{{ items[0] }}</li>
    <li>{{ items[1] }}</li>
    <li>{{ items[2] }}</li> -->
    <li @click="setFavourite(item)" v-for="item in itemsToDisplay">{{ item }}</li>
    <!-- <div v-for="item in items">{{ item }}</div> -->
  </ul>

  <p v-if="favourite">my favourit item is {{ favourite }}</p>

  <!-- v-for="item in array" -->


</template>

<script>
  export default {
    name: 'TList',
    props: {
      items: {
        type: Array,
        required: true
      },
      sort: {
        type: Boolean,
        default: false
      }
    },
    data () {
      return {
        favourite: ''
      }
    },
    computed: {
      noItems () {
        return !this.items.length
      },
      oneItem() {
        return this.items.length === 1
      },
      itemsToDisplay () {
        return !this.sort
          ? this.items.slice()
          : this.items.slice().sort((a, b) => a.localeCompare(b))
      }
    },
    methods: {
      setFavourite (par) {
        this.favourite = par
      }
    }
  }
</script>

<style scoped>
  ul {
    list-style-type: none;
    width: 300px;
    border: 1px solid black;
  }
</style>