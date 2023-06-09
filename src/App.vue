<template>
  <div class="sign-up-component">
    <section class="sign-up-component__header">
      <h1 class="sign-up-component__title">Learn to code by watching others</h1>
      <p class="sign-up-component__offer-description">See how experienced developers solve problems in real-time. Watching scripted tutorials are great, but understanding how developers think is invaluable</p>
    </section>
    <section class="sign-up-component__input-form">
      <PromoOffer>
        <template #span>
          Try it free 7 days
        </template>
        <template #price>
          then $20/mo. thereafter
        </template>
      </PromoOffer>
      <SignForm/>
    </section>
  </div>
</template>

<script lang="ts">
import SignForm from './widgets/SignForm.vue';
import PromoOffer from './components/PromoOffer.vue';

export default {
  components: {
    SignForm,
    PromoOffer,
},
}
</script>

<style scoped lang="scss">
.sign-up-component {
  display: flex;
  flex-direction: column;
  align-items: center;

  height: 100vh;
  overflow: auto;

  padding: 0rem 1.5rem;
  padding-top: 5.25rem;
  padding-bottom: 4.25rem;

  gap: 4.5rem;

  background-color: $red;
  background-image: url('@/assets/images/bg-intro-mobile.png');
  color: white;

  font-family: $poppins;

  text-align: center;

  &__header {
    display: flex;
    flex-direction: column;

    gap: 2rem;

    max-width: 540px;
  }

  &__title {
    padding: 0rem 3.5rem;

    font-size: 1.5rem;
    font-weight: 700;
  }

  &__offer-desciption {
    font-size: 1rem;
    font-weight: 500;
  }

  &__input-form {
    display: flex;
    flex-direction: column;

    gap: 1.5rem;

    max-width: 540px;
  }

  @media screen and (min-width: 768px) {
    background-image: url('@/assets/images/bg-intro-desktop.png');
    
    &__title {
      font-size: 2rem;
    }

    &__offer-desciption {
      font-size: .75rem;
    }

    &__input-form {
      display: flex;
      flex-direction: column;

      gap: 1.5rem
    }
  }

  @media screen and (min-width: 1024px) {
    flex-direction: row;
    align-items: center;
    justify-content: center;

    padding-left: 10.5rem;
    padding-right: 10.5rem;
    
    text-align: left;

    &__header {
      justify-content: center;
      
      width: 50%;
      max-width: 33.25rem;
      
      padding: 0;
    }
    
    &__title {
      padding-left: 0;

      font-size: 2.25rem;
    }

    &__offer-desciption {
      font-size: 1.5rem;
    }

    &__input-form {
      display: flex;
      flex-direction: column;

      width: 50%;
      max-width: 33.25rem;

      padding: 0;
    }
  }
}
</style>
