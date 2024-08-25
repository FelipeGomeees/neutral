<template>
    <div :class="inputClasses">
        <input 
        v-bind="$attrs"
        type="text" 
        placeholder=""
        class="n-input__input"
        />
        <label class="n-input__label">{{ label }}</label>
        <small class="n-input__small">{{ info }}</small>
    </div>
</template>
  
<script>
import './ninput.css';

export default {
  name: 'NInput',

  props: {
    label: {
      type: String,
    },
    info: {
      type: String,
    },
    basic: {
      type: Boolean,
    },
    size: {
      type: String,
      default: 'medium',
      validator: ((v) => {
        return ['small', 'large'].includes(v);
      })
    },
  },

  data() {
    return {
      // Reactive data can be defined here if needed
    };
  },

  computed: {
    inputClasses() {
      return {
        'n-input': true,
        'n-input--default': !this.basic,
        'n-input--basic': this.basic,
        'n-input--size-small': this.size === 'small',
        'n-input--size-large': this.size === 'large',
      };
    },
  },
};
</script>
  