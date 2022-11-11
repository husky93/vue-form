<template>
  <button :style="{background: color}" class="btn">{{text}}</button>
</template>

<script>
export default {
  name: 'ButtonElement',
  props: {
    text: String,
    color: String,
  },
};
</script>
