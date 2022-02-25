<template>
    <div>
        <form @submit.prevent="">
            <input type="text" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)">
        </form>
        <button @click="$emit('decr', count.id)">-</button>
        <div>{{ count.value }}</div>
        <button @click="$emit('incr', count.id)">+</button>
        <button @click="$emit('delete', count.id)">del</button>
    </div>
</template>

<script>
export default {
  name: "CounteR",
  props: {
    count: Object,
    modelValue: String
  },
  emits: ["delete", "incr", "decr"],
};
</script>

<style>

</style>