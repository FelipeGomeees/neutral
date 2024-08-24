<template>
    <div class="n-input">
        <input 
        v-bind="$attrs"
        type="text" 
        placeholder=""
        :class="inputClasses"
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
        'n-input__input': true,
        'n-input__input--default': !this.basic,
        'n-input__input--basic': this.basic,
        'n-input__input--s-small': this.size === 'small',
        'n-input__input--s-large': this.size === 'large',
      };
    },
  },
};
</script>
  