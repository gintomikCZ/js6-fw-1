<template>
  <div v-if="typeof num === 'string'">{{ num }}</div>
  <div v-else-if="num % 2" class="bg-pink">{{ num }}</div>
  <div v-else class="bg-green">{{ num }}</div>
</template>


<script>

export default {
  name: 'ASquare',
  props: {
    num: {
      validator: (v) => typeof v === 'string' || (typeof v === 'number' && !isNaN(v))
    }
  }
}

</script>
<style scoped>
div {
  height: 100px;
  width: 100px;
  box-sizing: border-box;
  border: 1px solid #cdcdcd;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 2rem;
}

.bg-pink {
  background: lightpink;
}
.bg-green {
  background: lightgreen;
}
</style>