<template>
    <div class="n-input">
        <input 
        v-bind="$attrs"
        type="text" 
        placeholder=""
        :class="inputClasses"
        />
        <label class="n-input__label">{{ label }}</label>
        <small class="n-input__small">{{ small }}</small>
    </div>
</template>
  
<script>
import './ninput.css';
import { reactive, computed } from 'vue';

export default {
  name: 'NInput',

  props: {
    label: {
      type: String,
    },
    small: {
      type: String,
    },
    basic: {
      type: Boolean,
    },
    size: {
      type: String,
      validator: function (value) {
        return ['small', 'medium', 'large'].includes(value);
      },
    },
  },

  emits: ['click'],

  data() {
    return {
      // Reactive data can be defined here if needed
    };
  },

  computed: {
    inputClasses() {
      return {
        'n-input__input': true,
        'n-input__input--default': !this.basic,
        'n-input__input--basic': this.basic,
      };
    },
  },

  methods: {
    onClick() {
      this.$emit('click');
    },
  },
};
</script>
  