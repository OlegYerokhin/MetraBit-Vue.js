<template>
  <div>
    <div v-html="logoHtml"></div>
    <button @click="$emit('update:showLoginPopUp', true)">LogIn</button>
  </div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    showLoginPopUp: {
      type: Boolean,
      default: true,
      required: true
    }
  },
  data: () => ({
    logoHtml: '<a href="#" style="display: block; margin: 5px "><img src="https://w7.pngwing.com/pngs/74/526/png-transparent-sign-of-the-horns-computer-icons-heavy-metal-music-rock-music-miscellaneous-text-hand.png" alt="Logo" style="width: 100px; heigth: 100px; "></a>',
  })
}
</script>
