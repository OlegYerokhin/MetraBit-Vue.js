<template>
  <div class="pop-up">
    <div class="pop-up__header">
      <button 
        class="pop-up__header-btn"
        @click="$emit('closePopUpEvent')"
      >X</button>
    </div>
    <div class="pop-up__main">

    </div>
    <div class="pop-up__footer">
      <button
        class="pop-up__footer-back button"
        @click="$emit('backPopUpEvent')"
      >Back</button>

      <button
        class="pop-up__footer-continue button"
        @click="$emit('continuePopUpEvent')"
      >Continue</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppPopUp',
}
</script>

<style lang="scss" scoped>
  .pop-up {
    position: relative;
    &__header-btn {
      font-family: cursive;
      border: none;
      background-color: transparent;
      font-weight: 700;
      position: absolute;
      right: 1px;
      bottom: 330px;
    }

    

    &__footer button {
      width: 70px;
      height: 40px;
      border-radius: 10px;
      display: block;
            cursor: pointer;

    }

    &__footer-back {
      background-color: cadetblue;
    }

    &__footer-continue {
      background-color: limegreen;
    }
  }
</style>