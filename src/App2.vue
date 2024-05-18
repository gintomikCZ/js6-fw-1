<template>

  <div class="container">
    <ASquare v-for="item in ar" :num="item" />
    <ASquare num="ahoj" />
  </div>

  <div>
    <TList :items="fruits" sort/>
  </div>
  <!-- <div>
    <TNameLabel
      firstName="John"
      lastName="Smith"
      title="Mr"
      dotAfterTitle
    />
    <TNameLabel
      firstName="Jane"
      lastName="Newman"
      title="Miss"
    />
  </div> -->

  <!-- <div>
    <TList :items="personsToDisplay" />
  </div> -->

  <ul>
    <li v-for="person in persons">
      <TNameLabel
        :firstName="person.firstName"
        :lastName="person.lastName"
        :title="person.title"
        :dotAfterTitle="person.dot"
      />
    </li>
  </ul>

</template>


<script>
import TList from '@/components/TList.vue'
import ASquare from '@/components/ASquare.vue'
import TNameLabel from '@/components/TNameLabel.vue'
export default {
  name: 'App',
  data () {
    return {
      ar: [19, 8, 56, 0, 12, 5],
      fruits: ['banán', 'jablko', 'čerešňa', 'jahoda', 'švestka', 'mrkev'],
      persons: [
        { firstName: 'John', lastName: 'Smith', title: 'Mr', dot: true },
        { firstName: 'Jane', lastName: 'Newman', title: 'Mrs', dot: false },
        { firstName: 'Peter', lastName: 'Something', title: 'Mr', dot: true },
      ]
    }
  },
  computed: {
    personsToDisplay () {
      return this.persons.map(person => {
        return person.title + (person.dot ? '. ' : ' ') + person.firstName + ' ' + person.lastName
      })
    }
  },
  components: { ASquare, TList, TNameLabel }
}

</script>


<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
}
</style>