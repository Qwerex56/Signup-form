<template>
  <div class="input-form">
    <div class="input-form__signup-input">
      <img :class="{'input-form__signup-input__err-img' : true}" src="@/assets/images/icon-error.svg" alt="ERR">
      <input class="input-form__signup-input__input"
        :class="{'error': true}"
        :type="inputType" 
        :value="modelValue" 
        @input="$emit('update:modelValue', ($event.target as HTMLInputElement).value)" 
        :placeholder="inputPlaceholder">
    </div>
    <p class="input-form__err-msg">
      <slot name="error-description"></slot>
    </p>
  </div>
</template>

<script lang="ts">
// import { useVuelidate } from '@vuelidate/core';
// import { required, alpha } from '@vuelidate/validators';

export default {
  // setup() {
  //   return {
  //     v$: useVuelidate(),
  //   };
  // },
  props: {
    modelValue: {
      type: String,
      required: false,
    },
    inputType: {
      type: String,
      required: true,
      default: 'text',
    },
    inputPlaceholder: {
      type: String,
      required: false,
      default: 'placeholder',
    },
  },
  emits: ['update:modelValue'],
  // validations() {
  //   return {
  //     modelValue: { required, alpha },
  //   }
  // }

}
</script>

<style scoped lang="scss">
.input-form {
  display: flex;
  flex-direction: column;
  position: relative;

  font-family: $poppins;

  &__signup-input {
    position: relative;

    &__input {
      -webkit-appearance: none;
      -moz-appearance: none;
      appearance: none;

      width: 100%;
  
      border: .0625rem solid $grayish-blue;
      border-radius: .125rem;
      outline: none;

      color: $dark-blue;
  
      font-size: 1rem;
      font-weight: 600;
      text-indent: 1rem;
      line-height: 300%;
      
      transition: 0.2s;
  
      &:focus, &:hover {
        border: .0625rem solid $blue;
      }

      &::placeholder {
        font-weight: 400;
      }

      &.error {
        border-color: $red;
        color: $red;
      }
    }

    &__err-img {
      position: absolute;
      justify-self: right;
      width: 1.5rem;

      margin-left: auto;

      right: 0px; top: 50%;
      transform: translate(-50%, -50%);
    }
  }

  &__err-msg {
    color: $red;
    
    font-size: 0.5rem;
    font-weight: 400;
    text-align: right;
  }
}
</style>