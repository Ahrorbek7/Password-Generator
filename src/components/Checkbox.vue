<template>
    <li class="flex cursor-pointer" @click="handleChange">
      <input type="checkbox" class="cursor-pointer bg-transparent" :checked="value" />
      <p>{{ label }}</p>
    </li>
  </template>
  
  <script>
  export default {
    name: 'Checkbox',
    props: ['label', 'value'],
    methods: {
      handleChange() {
        this.$emit('change', !this.value);
      },
    },
  };
  </script>