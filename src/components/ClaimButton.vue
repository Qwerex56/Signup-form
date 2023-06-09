<template>
  <button class="claim-button"
    @click="$emit('sendInput')">
    <slot name="description">
      Lorem, ipsum dolor.
    </slot>
  </button>
</template>

<script setup lang="ts">
defineEmits(['sendInput']);
</script>

<style scoped lang="scss">
.claim-button {
  width: 100%;
  height: 100%;

  border: none;
  border-radius: .5rem;

  box-shadow: 0rem .3125rem darken($green, $amount: 10%);

  background-color: $green;
  color: white;

  font-family: $poppins;
  font-size: 1rem;
  font-weight: 500;

  text-transform: uppercase;
  text-align: center;
  vertical-align: middle;

  line-height: 310%;

  transition: 0.2s;

  &:hover {
    background-color: lighten($green, $amount: 10%);
    box-shadow: 0rem .3125rem darken($green, $amount: 5%);
  }
}
</style>