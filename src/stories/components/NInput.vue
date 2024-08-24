<template>
    <div class="n-input">
        <input 
        v-bind="$attrs"
        type="text" 
        placeholder=""
        :class="classes"
        />
        <label class="n-input__label">{{ label }}</label>
        <small class="n-input__small">{{ small }}</small>
    </div>
</template>
  
  <script>
  import './ninput.css';
  import { reactive, computed } from 'vue';

//   defineOptions({
//   inheritAttrs: false
// })
  
  export default {
    name: 'NInput',
  
    props: {
      label: {
        type: String,
      },
      small: {
        type: String,
      },
      primary: {
        type: Boolean,
        default: false,
      },
      size: {
        type: String,
        validator: function (value) {
          return ['small', 'medium', 'large'].indexOf(value) !== -1;
        },
      },
      backgroundColor: {
        type: String,
      },
    },
  
    emits: ['click'],
  
    setup(props, { emit }) {
      props = reactive(props);
      return {
        classes: computed(() => ({
          'n-input__input ': true,
          'n-input__input--primary': props.primary,
          'n-input__input--secondary': !props.primary,
        //   [`storybook-button--${props.size || 'medium'}`]: true,
        })),
        onClick() {
          emit('click');
        },
      };
    },
  };
  </script>
  