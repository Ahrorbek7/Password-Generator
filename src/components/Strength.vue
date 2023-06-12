<template>
    <div class="password-strength items-center justify-between flex my-0 mx-4">
      <h4>STRENGTH</h4>
      <div class="strength-level flex items-center justify-evenly" :class="'strength-level-' + value">
        <h3 v-if="value === 1">TOO WEAK!</h3>
        <h3 v-else-if="value === 2">WEAK</h3>
        <h3 v-else-if="value === 3">MEDIUM</h3>
        <h3 v-else-if="value === 4">STRONG</h3>
        <h3 v-else>STRENGTH</h3>
        <span class="lvl-1"
          :class="{ 'red': value ===1, 'sub-red': value === 2,'yellow': value === 3,'green': value === 4}"></span>
        <span class="lvl-2" :class="{ 'sub-red': value === 2, 'yellow': value === 3,'green': value === 4 }"></span>
        <span class="lvl-3" :class="{ 'yellow': value === 3, 'green': value === 4 }"></span>
        <span class="lvl-4" :class="{ 'green': value === 4 }"></span>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Strength',
    props: ['value'],
  };
  </script>
  <style>
.strength-level-1 .lvl-1 { background-color: #FF4136; }
.strength-level-2 .lvl-1, .strength-level-2 .lvl-2 { background-color: #FF851B; }
.strength-level-3 .lvl-1, .strength-level-3 .lvl-2, .strength-level-3 .lvl-3 { background-color: #FFDC00; }
.strength-level-4 .lvl-1, .strength-level-4 .lvl-2, .strength-level-4 .lvl-3, .strength-level-4 .lvl-4 { background-color: #2ECC40; }
</style>