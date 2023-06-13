<template>
  <div class="container">
    <h1 class="title absolute">Password Generator</h1>
    <Output :value="passwordInput" />
    <div class="main-container absolute">
      <div class="password-length">
        <div class="length flex justify-between">
          <p>Character length</p>
          <h4 class="copied-span my- mx-2">{{ passwordLength }}</h4>
        </div>
        <input type="range" class="progress slider" min="4" :max="maxPasswordLength" step="1" :value="passwordLength" @input="updatePasswordLength" />
      </div>

      <div class="requirements flex flex-col justify-center">
        <ol>
          <Checkbox label="Include Uppercase Letters" :value="includeUppercase" @change="includeUppercase = $event" />
          <Checkbox label="Include Lowercase Letters" :value="includeLowercase" @change="includeLowercase = $event" />
          <Checkbox label="Include Numbers" :value="includeNumbers" @change="includeNumbers = $event" />
          <Checkbox label="Include Symbols" :value="includeSymbols" @change="includeSymbols = $event" />
        </ol>
      </div>

      <Strength :value="passwordDifficulty" />

      <Button :disabled-button="disabledButton" :generate-password="generatePassword" />
    </div>
  </div>
</template>

<script>
import Button from './components/Button.vue';
import Checkbox from './components/Checkbox.vue';
import Output from './components/Output.vue';
import Strength from './components/Strength.vue';

export default {
  name: 'App',
  components: {
    Button,
    Checkbox,
    Output,
    Strength,
  },
  data() {
    return {
      passwordInput: '',
      passwordLength: 8,
      includeLowercase: true,
      includeUppercase: false,
      includeNumbers: false,
      includeSymbols: false,
    };
  },
  computed: {
    chars() {
      let chars = '';
      if (this.includeLowercase) chars += 'abcdefghijklmnopqrstuvwxyz';
      if (this.includeUppercase) chars += 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
      if (this.includeNumbers) chars += '0123456789';
      if (this.includeSymbols) chars += '!@#$%^&*()_+-=[]{}|;:,.<>/?';
      return chars;
    },
    passwordDifficulty() {
      let difficulty = 0;
      if (this.includeLowercase) {
        difficulty++;
      }
      if (this.includeUppercase) {
        difficulty++;
      }
      if (this.includeNumbers) {
        difficulty++;
      }
      if (this.includeSymbols) {
        difficulty++;
      }
      return difficulty;
    },
    disabledButton() {
      return !(this.includeLowercase || this.includeUppercase || this.includeNumbers || this.includeSymbols);
    },
    maxPasswordLength() {
      const charsCount = this.chars.length;
      return Math.min(Math.floor(charsCount ** this.passwordLength), 16);
    },
  },
  methods: {
    generatePassword() {
      let password = '';
      for (let i = 0; i < this.passwordLength; i++) {
        const randomIndex = Math.floor(Math.random() * this.chars.length);
        password += this.chars[randomIndex];
      }
      this.passwordInput = password;
    },
    updatePasswordLength(event) {
      this.passwordLength = parseInt(event.target.value);
    },
  },
};
</script>

<style>
.red {
  background-color: #f72e2e;
  border: none !important;
}
.sub-red {
  background-color: #fd6c44;
  border: none !important;
}
.yellow {
  background-color: #F8CD65;
  border: none !important;
}

.green {
  background-color: #A4FFAF;
  border: none !important;
}
input[type="range"] {
  -webkit-appearance: none;
  appearance: none; 
  height:10px;
  width: 93%;
  margin: 0 1rem;
  cursor: pointer;
  outline: none;
  border-radius: 16px;
  overflow: hidden;
}

input[type="range"]::-webkit-slider-runnable-track {
  background: #18171F;
  border-radius: 16px;
  width: 200px !important;
}

input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none; 
  height: 12px;
  width: 12px;
  background-color: #fff;
  border-radius: 50%;
  border: 2px solid #ffffff;
  box-shadow: -407px 0 0 400px #A4FFAF;
}
input[type="range"]::-webkit-slider-thumb:hover{
  background-color: #18171F;
  border: 2px solid #A4FFAF;
}
</style>
