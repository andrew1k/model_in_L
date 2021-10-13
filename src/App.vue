<template>
  <div class="container">
    <form class="card" @submit.prevent="submitHandler">
      <h1>Анкета на Vue разработчика!</h1>
      <div class="form-control">
        <label for="name">Как тебя зовут?</label>
        <input 
        type="text" 
        id="name" 
        placeholder="Введи имя"
        v-model.trim="name"
        >
        <small v-if="errors.name">{{ errors.name }}</small>
      </div>

      <div class="form-control">
        <label for="age">Выбери возраст</label>
        <input 
        type="number" 
        id="age" 
        v-model.number="age"
        max="70"
        >
      </div>

      <div class="form-control">
        <label for="city">Твой город</label>
        <select id="city" v-model="city">
          <option value="spb">Санкт-Петербург</option>
          <option value="msk">Москва</option>
          <option value="kzn">Казань</option>
          <option value="nsk">Новосибирск</option>
        </select>
      </div>

      <div class="form-checkbox">
        <span class="label">Готов к переезду в Токио?</span>
        <div class="checkbox">
          <label><input type="radio" v-model="relocate" name="trip" value="yes"/> Да</label>
        </div>

        <div class="checkbox">
          <label><input type="radio" v-model="relocate" name="trip" value="no"/> Нет</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Что знаешь во Vue?</span>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" name="skills" value="vuex"/> Vuex</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" name="skills" value="cli"/> Vue CLI</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" name="skills" value="router"/> Vue Router</label>
        </div>
      </div>

      <button type="submit" class="btn primary">Отправить</button>
    </form>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        name: '',
        age: 23,
        city: 'kzn',
        relocate: null,
        skills: [],
        errors: {
          name: null
        }
      }
    },
    methods: {
      formIsValid() {
        let isValid = true
        if (this.name.length === 0) {
          this.errors.name = `Can't be empty`
          isValid = false
          return isValid
        }
      },
      submitHandler() {
        if (this.formIsValid()) {
        console.group('Form Data')
          console.log('name', this.name)
          console.log('age', this.age)
          console.log('city', this.city)
          console.log('relocate', this.relocate)
          console.log('skills', this.skills)
        console.groupEnd()
        }
      }
    },
  }
</script>

<style>

</style>
