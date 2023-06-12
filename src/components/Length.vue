html
<template>
  <div class="password-length">
    <div class="length flex justify-between">
      <p>Character length</p>
      <h4 class="copied-span my- mx-2">{{ value }}</h4>
    </div>
    <input type="range" class="progress slider" min="4" :max="max" step="1" :value="value" @input="$emit('update:value', $event.target.value)" />
  </div>
</template>

<script>
export default {
  name: 'Length',
  props: ['value', 'max', 'passwordLength'],
  computed: {
    Length() {
      return this.passwordLength;
    }
  },
};
</script>