<template>
  <div class="container">
    <hr>
    <h4 class="title">
      Тип подчключения:
    </h4>
    <div class="card">
      <div class="card__left">
        <h3 class="card__title">
          {{data[0].variants[0].title}}
        </h3>
        <div v-for="(item,key) in data[0].variants[0].description.split('\n')" :key="key">
        <p>
          {{item}}
        </p>

        </div>
      </div>
      <div class="card__right">
        <span class="card__price">
          400 Р
        </span>
        <form class="card__form">
          <div  class="card__input-cable input" v-for="(item,key) in data[0].variants[0].options" :key="key">
            <input v-model="input[key]" type="checkbox" :id="key">
            <label :for="key">{{item.title}}</label>
          </div>
          
          <button v-on:click.prevent="click" class="card__submit">Выбрано</button>
        </form>
      </div>
    </div>
  </div>
  <pre>
    {{data}}
  </pre>
</template>

<script>
import db from "@/assets/db/db.json"
export default {
    data(){
      return {
        data:db,
        input:{},
      }
    },
    methods: {
      click() {
        console.log(this.input)
      }  
    },
    computed :{
      test(){
        console.log(data[0].variants[0].options[this.input])
      }
    },
    watch: {
      input: {
            deep: true,
            handler(newValue, oldValue) {
                this.click()
            }
        }
    
    }
}
</script>

<style>

</style>