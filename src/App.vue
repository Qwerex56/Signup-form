<template>
  <div>
    Hello world
    <InputForm v-model="someVal"></InputForm>
  </div>
</template>

<script lang="ts">
import InputForm from './components/InputForm.vue';

export default {
  components: {
    InputForm,
  },
  data() {
    return {
      someVal: '',
    }
  }
}
</script>

<style scoped lang="scss">
</style>
