<template>

<div>{{ nameToDisplay }}</div>

</template>

<script>

export default {
  name: 'TNameLabel',
  props: {
    firstName: String,
    lastName: String,
    title: String,
    dotAfterTitle: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    // propertyName () { return value } ... klíčové slovo this
    nameToDisplay () {
      // return this.title + (this.dotAfterTitle ? '. ' : ' ') + this.firstName + ' ' + this.lastName
      let result = this.title
      if (this.dotAfterTitle) {
        result += '.'
      }
      result += ' ' + this.firstName + ' ' + this.lastName
      return result
    }
  }
}

</script>