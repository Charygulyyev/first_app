<template>
  <input type="number" v-model="new_counter">
  <button @click="add_counter">add</button>
  <br />
  <template v-for="(count, ind) in counters" :key="ind">
    <Counter :count="count"/>
    <button @click="delete_counter(ind)">delete</button>
    <hr v-if="ind+1 < get_length"/>
  </template>
</template>

<script>
import Counter from './Counter.vue'
export default {
name: 'GreeT',
components: {
  Counter
},
data(){
  return{
    new_counter: 0,
    counters: [],
  }
},
computed:{
  get_length(){
    return this.counters.length
  }
},
methods:{
  add_counter(){
    this.counters = [...this.counters,this.new_counter]
    this.new_counter = 0
  },
  delete_counter(par){
    this.counters = this.counters.filter( (e,i) => i !== par )
  }
}
}
</script>

<style>
</style>