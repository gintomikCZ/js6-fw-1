<template>

<div>
  <TSlider :content="fruits"/>
</div>

<div>
  <TList :items="fruits" />
</div>

<TButton label="click me!" @clicked="onClicked" />

<div>
  <TButton
    v-for="city in cities"
    :label="city"
    @clicked="onCityClicked"
  />
</div>

<div>
  <ASquare v-for="item in [12, 7, 9, 14, 68]" :num="item"/>
</div>

</template>

<script>

import TSlider from '@/components/TSlider.vue'
import TList from '@/components/TList.vue'
import TButton from '@/components/TButton.vue'
import ASquare from '@/components/ASquare.vue'

export default {
  name: 'App',
  data() {
    return {
      fruits: ['kiwi', 'pomeranč', 'banán', 'mrkev', 'okurka'],
      cities: ['Brno', 'Praha', 'Ostrava']
    }
  },
  methods: {
    onClicked (par) {
      console.log(par)
    },
    onCityClicked (payload) {
      console.log('user clicked on city: ' + payload)
    }
  },
  components: { TSlider, TList, TButton, ASquare }
}

</script>

<style>
.bg-pink {
  background: lightpink;
}
</style>