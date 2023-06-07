<template>
  <div class="sign-form">
    <InputForm 
      v-for="form in inputsArr" :key="form.id"
      :input-type="form.inputType"
      :input-placeholder="form.placeholder">
    </InputForm>
    <ClaimButton>
      <template #description>Claim your free trial</template>
    </ClaimButton>
    <p class="sign-form__terms">
      By clicking the button, you are agreeing to our 
      <span class="sign-form__terms--span">Terms and Services</span>
    </p>
  </div>
</template>

<script lang="ts">
import InputForm from '@/components/InputForm.vue';
import ClaimButton from '@/components/ClaimButton.vue';

export default {
  components: {
    InputForm,
    ClaimButton,
  },
  data() {
    return {
      inputsArr: [
        {
          id: 0,
          // modelValue: ,
          inputType: 'text',
          placeholder: 'First Name',
        },
        {
          id: 1,
          // modelValue: ,
          inputType: 'text',
          placeholder: 'Last Name',
        },
        {
          id: 2,
          // modelValue: ,
          inputType: 'email',
          placeholder: 'Email Address',
        },
        {
          id: 3,
          // modelValue: ,
          inputType: 'password',
          placeholder: 'Password',
        },
      ],
    }
  }
}
</script>

<style lang="scss">
.sign-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;

  padding: 1.5rem;

  border-radius: .625rem;

  background-color: white;
  color: $grayish-blue;

  &__terms {
    padding: 0rem .75rem;

    font-family: $poppins;
    font-size: .75rem;
    font-weight: 500;

    text-align: center;

    &--span {
      color: $red;
      font-weight: 700;
    }
  }
}
</style>