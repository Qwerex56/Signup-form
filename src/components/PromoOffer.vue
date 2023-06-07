<template>
  <p class="promo-offer">
    <span class="promo-offer__span">
      <slot name="span">Lorem, ipsum dolor. </slot>
    </span>
    <slot name="price">Lorem, ipsum dolor.</slot>
  </p>
</template>

<script lang="ts">
export default {
  
}
</script>

<style scoped lang="scss">
.promo-offer {
  padding: 1.5rem 5rem;

  border-radius: .5rem;
  box-shadow: 0rem .375rem transparentize($dark-blue, $amount: 0.6);

  background-color: $blue;
  color: white;

  font-size: 0.75rem;
  font-family: $poppins;
  font-weight: 500;

  text-align: center;

  &__span {
    font-weight: 700;
  }
}
</style>