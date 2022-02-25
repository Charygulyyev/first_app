<template>
  <form @submit.prevent="add_counter">
    <input type="number" v-model.lazy="new_counter.value">
    <button @click.prevent="add_counter">add</button>
  </form>
  <hr />
  <template v-for="(count, ind) in counters" :key="count.id">
    <Counter 
      :count="count"
      @incr="incr_counter"
      @decr="decr_counter"
      @delete="delete_counter"
      v-model="name"
      />
    <hr v-if="ind+1 < get_length"/>
  </template>
</template>

<script>
import Counter from './Counter.vue'

export default {

name: 'CounterS',
components: {
  Counter
},

data(){
  return{
    new_counter: {
      id: '',
      value: 0,
    },
    counters: [],
    name: "",
  }
},

computed:{
  get_length(){
    return this.counters.length
  }
},

methods:{
  incr_counter(id){
    this.counters.map(counter => {
      if (counter.id === id){
        counter.value += 1
      }
    })
  },

  decr_counter(id){
    this.counters.map(counter => {
      if (counter.id === id){
        counter.value -= 1
      }
    })
  },

  uuid(){
    let timeStamp = new Date;
    let id = 
      timeStamp.getFullYear() + '/' + 
      timeStamp.getMonth() + '/' + 
      timeStamp.getDate() + '/' +
      timeStamp.getMilliseconds() + ':' +
      timeStamp.getSeconds() + ':' +
      timeStamp.getMinutes() + ':' +
      timeStamp.getHours();
    this.new_counter.id = id
  },

  add_counter(){
    this.uuid();
    this.counters = [this.new_counter, ...this.counters];
    this.new_counter = {
      id: '',
      value: 0
    }
  },

  delete_counter(par){
    this.counters = this.counters.filter( (e) => e.id !== par )
  }
}
}
</script>

<style>
</style>