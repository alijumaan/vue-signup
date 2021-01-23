<template>
  <button
      :style="{color, background}"
      :disabled="disabled">{{ text }}</button>
</template>

<script>
export default {
  props: {
    text: {type: String, required: true},
    color: {type: String},
    background: {type: String},
    disabled: {type: Boolean, required: true}
  }
}
</script>

<style scoped>
button:disabled {
  opacity: .5;
}
button {
  border: none;
  padding: 5px;
  border-radius: 5px;
  width: 100%;
}
button:hover {
  filter: brightness(150%);
}
</style>
