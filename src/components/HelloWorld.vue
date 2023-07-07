<template>
  <div>
    <input type="text" placeholder="Input link here" v-model="name"> |
    <button @click="getLink()">Generate shortened link</button>
    <hr>
    <h1>{{ name }}</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      name: ''
    }
  },
  methods: {
    getLink() {
      return
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
