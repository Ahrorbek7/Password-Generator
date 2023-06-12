<template>
    <button class="btn-generate cursor-pointer my-4 mx-4" @click="generatePassword" type="button" :disabled="disabledButton">
      GENERATE
      <i class="bi bi-arrow-right"></i>
    </button>
  </template>
  
  <script>
  export default {
    name: 'Button',
    props: ['disabledButton', 'generatePassword'],
  };
  </script> 