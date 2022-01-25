<template>
  <div>
    <div v-html="linkToMyProfile"></div>
  </div>
</template>

<script>
export default {
  name: 'Footer',
  data: () => ({
    linkToMyProfile: '<p>Created by <a href="https://github.com/OlegYerokhin/MetraBit">Me</a></p>'
  })
}
</script>

<style lang="scss" scoped>

</style>