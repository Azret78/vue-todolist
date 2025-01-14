<template>
  <div class="container">
    <div class="card">
      <h1>Добавьте заметку</h1>
      <div class="card__works">
        <div class="card__btns">
          <app-button @click="filterActive">Отсортировать по активным</app-button>
          <app-button @click="toggleFilter">Показать все</app-button>
        </div>
        <div class="card__work">
          <p>Название: <b>{{ workName }}</b></p>
        </div>
        <div class="card__work">
          <p>Описание: <b>{{ workText }}</b></p>
        </div>
      </div>
      <form @submit.prevent="">
        <app-input v-model:value="workName" placeholder="Введите название"></app-input>
        <app-input v-model:value="workText" placeholder="Введите описание"></app-input>
        <app-button type="primary" :disabled="workName.length === 0 || workText.length === 0"
          @click="addWork">Добавить</app-button>
      </form>
    </div>
    <div class="card">
      <h2>Список всех заметок</h2>
      <app-button :type="isActive && works.length !== 0 ? 'danger' : 'primary'" @click="drop"
        v-if="works.length !== 0">{{ isActive && works.length !== 0 ? "Скрыть" : "Показать" }} список</app-button>
      <p v-else><small>Список пуст</small></p>
      <app-list v-if="isActive && works.length !== 0" :works="filteredWorks"></app-list>
    </div>
  </div>
</template>

<script>
import AppList from '@/components/AppList.vue';
import AppButton from '@/components/UI/AppButton.vue';
import AppInput from '@/components/UI/AppInput.vue';

export default {
  data() {
    return {
      works: [
        { workName: 'Первая задача', workText: 'Далеко-далеко за словесными горами в стране гласных и согласных живут, рыбные тексты. Рыбными которой использовало не снова рыбного деревни знаках текстами необходимыми встретил! Дал строчка которое грустный грамматики наш ipsum, своих великий?', classActive: false },
        { workName: 'Вторая задача', workText: 'Далеко-далеко за словесными горами в стране гласных и согласных живут, рыбные тексты. Рыбными которой использовало не снова рыбного деревни знаках текстами необходимыми встретил! Дал строчка которое грустный грамматики наш ipsum, своих великий?', classActive: true },
        { workName: 'Третья задача', workText: 'Далеко-далеко за словесными горами в стране гласных и согласных живут, рыбные тексты. Рыбными которой использовало не снова рыбного деревни знаках текстами необходимыми встретил! Дал строчка которое грустный грамматики наш ipsum, своих великий?', classActive: true },
        { workName: 'Четвёртая задача', workText: 'Далеко-далеко за словесными горами в стране гласных и согласных живут, рыбные тексты. Рыбными которой использовало не снова рыбного деревни знаках текстами необходимыми встретил! Дал строчка которое грустный грамматики наш ipsum, своих великий?', classActive: false }
      ],
      isActive: true,
      workName: '',
      workText: '',
      filteredWorks: [],
      // classActive: true,
    }
  },
  // provide () {
  //   return {
      // classActive: true
    // }
  // },
  methods: {
    drop() {
      this.isActive = !this.isActive
    },
    addWork() {
      this.works.push({ workName: this.workName, workText: this.workText })
      this.workName = ''
      this.workText = ''
    },
    filterActive() {
      this.filteredWorks = this.works.filter(work => work.classActive);
    },
    toggleFilter() {
      this.filteredWorks = this.works
    }
  },
  mounted() {
    this.filteredWorks = this.works;
  },
  components: {
    AppList, AppButton, AppInput
  }
}
</script>

<style scoped>
form {
  margin-top: 20px;
}

.card__works {
  display: flex;
  flex-direction: column;
  align-self: start;
  text-align: left;
}

.card__work {
  display: flex;
}

.card__work p:first-letter {
  text-transform: uppercase;
}
</style>
