<template>
  <ul class="work__list">
    <app-item v-for="(work, idx) in works" :key="idx" :work="work" :classActive="work.classActive" @splice="deleteWork(idx)" @toActive="fromActive(idx)"></app-item>
  </ul>
</template>

<script>
import AppItem from './AppItem.vue'
export default {
  props: ['works', 'classActive'],
  components: { AppItem },
  methods: {
    deleteWork(idx) {
      this.works.splice(idx, 1);
    },
    fromActive(idx) {
      this.works[idx].classActive = !this.works[idx].classActive;
    }
  }
}
</script>

<style scoped>
.work__list {
  text-align: left;
  display: flex;
  flex-direction: column;
  gap: 20px;
}
</style>