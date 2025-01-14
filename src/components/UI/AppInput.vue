<template>
  <div class="form-control">
    <label></label>
    <input type="text" :placeholder="placeholder" :value="value" @input="change">
  </div>
</template>

<script>
export default {
  emits: ['update:value'],
  props: {
    placeholder: String,
    value: String
  },
  methods: {
    change(event) {
      this.$emit('update:value', event.target.value)
      console.log(event.target.value)
    }
  }
}
</script>

<style scoped></style>