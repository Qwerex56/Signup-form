<template>
  <div class="input-form" :class="{ 'error' : hasError() }" @animationend="handleAnimationEnd()">
    <div class="input-form__signup-input">
      <img class="input-form__signup-input__err-img" src="@/assets/images/icon-error.svg" alt="ERR">
      <input class="input-form__signup-input__input"
        v-model="value"
        :name="name"
        :type="inputType"
        :placeholder="inputPlaceholder">
    </div>
    <p class="input-form__err-msg">
      {{ errorMessage }}
    </p>
  </div>
</template>

<script setup lang="ts">
import { useField } from 'vee-validate';

function hasError() {
  return errors.value.length > 0;
}

function handleAnimationEnd() {

}

const props = defineProps({
  inputType: {
    type: String,
    default: 'text',
  },
  inputPlaceholder: {
    type: String,
    default: '',
  },
  name: {
    type: String,
    required: true,
  }
});

const { value, errors, errorMessage } = useField(() => props.name)
</script>

<style scoped lang="scss">
.input-form {
  display: flex;
  flex-direction: column;
  position: relative;

  font-family: $poppins;

  &__signup-input {
    position: relative;

    z-index: 1;
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
    }

    &__err-img {
      position: absolute;
      justify-self: right;
      width: 1.625rem;
      margin-left: auto;

      right: 0px; top: 50%;
      transform: translate(-50%, -50%);

      visibility: hidden;
    }
  }

  &__err-msg {
    color: $red;
    
    font-size: .75rem;
    font-weight: 400;
    font-style: italic;
    text-align: right;
  }
}

.error.input-form {
  .input-form {
    &__signup-input {
      &__input {
        border: .0625rem solid $red;
        color: $red;
      }

      &__err-img {
        visibility: visible;
      }
    }

    &__err-msg {
      animation: slideMsg 0.2s forwards linear 1;
    }
  }

  animation: scrollDown 0.2s forwards linear 1;
}

@keyframes scrollDown {
  0% {
    height: 3.4375rem;
  }

  100% {
    height: 4.5625rem;
  }
}

@keyframes slideMsg {
  0% {
    transform: translateY(-100%);
  }

  100% {
    transform: translateY(0%);
  }
}
</style>