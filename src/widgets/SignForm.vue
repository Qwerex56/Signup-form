<template>
  <div class="sign-form">
    <InputForm
      v-for="form in inputArr" :key="form.id"
      :name="form.name"
      :input-type="form.inputType"
      :input-placeholder="form.placeholder">
    </InputForm>
    <ClaimButton @send-input="callForm()">
      <template #description>Claim your free trial</template>
    </ClaimButton>
    <p class="sign-form__terms">
      By clicking the button, you are agreeing to our 
      <span class="sign-form__terms--span">Terms and Services</span>
    </p>
  </div>
</template>

<script setup lang="ts">
import InputForm from '@/components/InputForm.vue';
import ClaimButton from '@/components/ClaimButton.vue';

import { ref } from 'vue';
import { useForm } from 'vee-validate';
import * as yup from 'yup';

interface ISignupForm {
  name: string, 
  lastName: string,
  email: string,
  password: string,
};

const signupSchema = yup.object({
  name: yup.string().required('First Name cannot be empty'),
  lastName: yup.string().required('Last Name cannot be empty'),
  email: yup.string().required('Email cannot be empty').email('Looks like this is not an email'),
  password: yup.string().required('Password cannot be empty'),
})

const { validate } = useForm<ISignupForm>({
  validationSchema: signupSchema,
});

function callForm() {
  validate();
}

const inputArr = ref([
  {
    id: 0,
    inputType: 'text',
    placeholder: 'First Name',
    name: 'name',
  },
  {
    id: 1,
    inputType: 'text',
    placeholder: 'Last Name',
    name: 'lastName',
  },
  {
    id: 2,
    inputType: 'email',
    placeholder: 'Email Address',
    name: 'email',
  },
  {
    id: 3,
    inputType: 'password',
    placeholder: 'Password',
    name: 'password',
  },
]);
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
    font-size: 12px;
    font-weight: 500;

    text-align: center;

    line-height: 1.5rem;

    &--span {
      color: $red;
      font-weight: 700;
    }
  }
}
</style>