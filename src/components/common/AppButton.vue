<template>
  <div class="app-button">
    <button
      class="app-button__btn" 
      @click="$emit('appButtonClick')"
    >Click Me!</button>
  </div>
</template>

<script>
export default {
  name: 'AppButton',
}
</script>

<style lang="scss" scoped>
  .app-button {
    &__btn {
      cursor: pointer;
      border: 2px solid #000;
      border-radius: 50%;
      background-color: #ffc400;
      font-size: 16px;
      font-weight: 700;
      width: 55px;
      height: 55px;
    }
  }
</style>