<template>
  <button @click="decr">-</button>
  <div>{{c}}</div>
  <button @click="incr">+</button>
</template>

<script>
export default {
name: 'CounteR',
props: {
    count: Number,
},
data(){
    return {
        c: this.count
    }
},
methods:{
    decr(){
        this.c -= 1
    },
    incr(){
        this.c += 1
    }
}
}
</script>

<style>

</style>