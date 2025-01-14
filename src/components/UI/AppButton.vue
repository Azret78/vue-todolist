<template>
  <button class="btn" :class="type">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      validator(val) {
        return ['primary', 'danger', 'warning'].includes(val)
      }
    }
  }
}
</script>

<style scoped></style>