<template>
  <div class="post-card">
    <h2 class="post-card__title">{{ post.title }}</h2>
    <div class="post-card__body">{{ formattedText(post.body) }}</div>
    <button class="post-card__read-more">Read More</button>
  </div>
</template>

<script>
export default {
  name: "PostCard",
  props: {
    post: {
      type: Object,
      required: true,
      default: () => ({
        userId: 1,
        id: 1,
        title: 'Some default title',
        body: 'Some default text'
      }),
      validator: function(value) {
        return value ? true : false
        
      },
    },
  },
  data: () => ({
    
  }),

  methods: {
    formattedText(text) {
      if(text.length > 120) {
        let updatedText = text.slice(0, 120) + '...'

        return updatedText
      }
    }
  }
}
</script>

<style scoped lang="scss">
  .post-card {
    border: 1px solid #000;
    max-width: 600px;
    padding: 25px;
    &__title {
      margin-bottom: 15px;
    }
    &__body {
      margin-bottom: 15px;
    }
    &__read-more {
      border: none;
      font-size: 16px;
      color: cornflowerblue;
      cursor: pointer;
      background: transparent;

    }
  }
</style>