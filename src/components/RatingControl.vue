<template>
  <ul>
    <li :class="{ active: modelValue === 'poor' }">
      <button type="button" @click="activate('poor')">Poor</button>
    </li>
    <li :class="{ active: modelValue === 'average' }">
      <button type="button" @click="activate('average')">Average</button>
    </li>
    <li :class="{ active: modelValue === 'good' }">
      <button type="button" @click="activate('good')">Good</button>
    </li>
  </ul>
</template>

<script>
export default {
    props: ['modelValue'],
    emits:['update:modelValue'],
//   data() {
//     return {
//       activeOptions: null,
//     };
//   },
// computed:{
//     activeOptions() {
//     return this.modelValue
//     }
// },
  methods: {
    activate(options) {
      
      this.$emit('update:modelValue', options)
    },
  },
};
</script>

<style scoped>
.active {
  border-color: rgba(128, 0, 73, 0.287);
}
.active button {
  color: rgba(128, 0, 73, 0.287);
}

ul {
  list-style: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
}
li {
  margin: 0 1rem;
  border: 1px solid #ccc;
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}
button {
  font: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
</style>