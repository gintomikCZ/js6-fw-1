<template>
  <h1>frameworks 1</h1>
  <TList :items="fruits" />
  <!-- <TComponent myProp="10"/> -->
  <div>{{ 24 + 78}}</div>
  <TList :items="cities" />
  <TButton v-for="city in cities" :label="city" />

  <template v-for="(fruitName, index) in fruits">
    <h3>{{ fruitName }}</h3>
    <p>{{ 'the best fruit ever is ' + fruitName }}</p>
  </template>

</template>

<script>

import TList from '@/components/TList.vue'
import TButton from '@/components/TButton.vue'
export default {
  name: 'App' ,
  data () {
    return {
      key1: 'value',
      key2: 'value2',
      fruits: ['hruška', 'banán', 'jablko'],
      cities: ['Praha', 'Brno', 'Londýn', 'Paříž']
    }
  },
  components: { TList, TButton }
}

</script>