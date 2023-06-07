<template>
  <div class="sign-up-component">
    <section>
      <h1 class="sign-up-component__title">Learn to code by watching others</h1>
      <p class="sign-up-component__offer-description">See how experienced developers solve problems in real-time. Watching scripted tutorials are great, but understanding how developers think is invaluable</p>
    </section>
    <PromoOffer>
      <template #span>
        Try it free 7 days
      </template>
      <template #price>
        then $20/mo. thereafter
      </template>
    </PromoOffer>
    <SignForm/>
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
  data() {
    return {
      someVal: '',
    }
  }
}
</script>

<style scoped lang="scss">
.sign-up-component {
  display: flex;
  flex-direction: column;

  height: 100vh;
  overflow: auto;

  padding: 0rem 1.5rem;
  padding-top: 6.25rem;
  padding-bottom: 4.25rem;

  gap: 1.5rem;

  background-color: $red;
  background-image: url('@/assets/images/bg-intro-mobile.png');
  color: white;

  font-family: $poppins;

  text-align: center;

  &__title {
    font-size: 1.5rem;
    font-weight: 700;
  }

  &__offer-desciption {
    font-size: 16px;
    font-weight: 500;
  }
}
</style>
