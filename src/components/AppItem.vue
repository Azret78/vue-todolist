<template>
  <li :class="classActive ? 'active' : ''">
    <p>{{ work.workName }}</p>
    <p>{{ work.workText }}</p>
    <div class="btns">
      <app-button type="danger" @click="$emit('splice')">Удалить</app-button>
      <app-button :type="classActive ? 'primary' : 'warning'" @click="$emit('toActive')">Сделать {{ classActive ? 'неактивной' :
        'активной' }}</app-button>
    </div>
  </li>
  <hr>
</template>

<script>
import AppButton from './UI/AppButton.vue'
export default {
  // inject: ['classActive'],
  emits: ['splice', 'toActive'],
  props: ['work', 'classActive'],
  methods: {
    // toActive() {
    //   this.classActive = !this.classActive
    // }
  },
  components: { AppButton },
}
</script>

<style scoped>
.work__list p {
  margin: 0;
}

.work__list p:first-child {
  font-size: 24px;
}

.work__list li {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.work__list li .btns {
  align-self: end;
  display: flex;
  align-items: center;
  gap: 10px;
}
</style>