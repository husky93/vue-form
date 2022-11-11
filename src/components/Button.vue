<template>
  <button @click="onClick()" :style="{background: color}">{{text}}</button>
</template>

<script>
export default {
  name: 'ButtonElement',
  props: {
    text: String,
    color: String,
  },
  methods: {
    onClick() {
      this.$emit('toggle-add-task')
    },
  },
};
</script>

<style scoped>
button {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
</style>
