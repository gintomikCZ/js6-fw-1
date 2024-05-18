<template>
  <button @click="onClick">{{ label }}</button>
</template>

<script>

export default {
  name: 'TButton',
  props: {
    label: String
  },
  methods: {
    onClick() {
      this.$emit('clicked', this.label)
    }
  }
}

</script>

<style scoped>
button {
  background: white;
  transition: background-color .3s ease;
  border: 1px solid black;
  padding: .35em .7em
}
button:hover {
  background: lightpink;
}
</style>