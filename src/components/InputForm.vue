<template>
  <div class="input-form">
    <div class="input-form__signup-input">
      <img v-if="false" class="input-form__signup-input__err-img" src="@/assets/images/icon-error.svg" alt="ERR">
      <input class="input-form__signup-input__input"
        :class="{'error': false}"
        :type="inputType" 
        :value="modelValue" 
        @input="$emit('update:modelValue', ($event.target as HTMLInputElement).value)" 
        :placeholder="inputPlaceholder">
    </div>
    <p v-if="false" class="input-form__err-msg">
      <slot name="error-description">Error MSG</slot>
    </p>
  </div>
</template>

<script lang="ts">
export default {
  props: {
    modelValue: {
      type: String,
      required: false,
    },
    inputType: {
      type: String,
      required: false,
      default: 'text',
    },
    inputPlaceholder: {
      type: String,
      required: false,
      default: 'placeholder',
    },
  },
  emits: ['update:modelValue'],
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
      border-radius: .25rem;
      outline: none;

      color: $dark-blue;
  
      font-size: .75rem;
      font-weight: 700;
      text-indent: 1.25rem;
      line-height: 440%;
      
      transition: 0.2s;
  
      &:focus, &:hover {
        border: .0625rem solid $blue;
      }

      &::placeholder {
        font-weight: 700;
      }

      &.error {
        border: .125rem solid $red;

        color: $red;
      }
    }

    &__err-img {
      position: absolute;
      justify-self: right;
      width: 1.625rem;

      margin-left: auto;

      right: 0px; top: 50%;
      transform: translate(-50%, -50%);
    }
  }

  &__err-msg {
    color: $red;
    
    font-size: 12px;
    font-weight: 400;
    font-style: italic;
    text-align: right;
  }
}
</style>