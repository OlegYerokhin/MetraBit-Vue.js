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
  data: () => ({
    post: {
      userId: 1,
      id: 2,
      title: 'Sunt aut facere repellat provident occaecati excepturi optio reprehenderit',
      body: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. In accusamus ratione ipsum est possimus, libero porro maxime enim perspiciatis distinctio quam neque repudiandae sequi a ut beatae illo ab quod! Minus, nesciunt ullam non beatae expedita repudiandae, voluptatibus est unde quas vero consequuntur. Esse, officiis ea. Amet iusto similique, reprehenderit perspiciatis quod consequuntur cupiditate magnam, esse, modi quos numquam harum libero reiciendis voluptates necessitatibus id repellat consequatur labore. Recusandae beatae eum earum vero officia dolor, accusantium expedita optio voluptas eos quas repellendus quae repellat ducimus ipsam voluptatum delectus rem totam! Accusantium pariatur exercitationem nesciunt necessitatibus, similique ea nobis quaerat consectetur tempora eum soluta autem temporibus quibusdam deserunt dolor saepe accusamus voluptate quo quod quia debitis. Dolorum corporis perferendis illo iure! Sunt, cum. Dolor explicabo voluptas fugiat asperiores quisquam ex rem. Earum ducimus maxime laborum cumque accusantium tenetur. Illum, aperiam, est modi itaque minima officiis odit blanditiis, voluptate facere expedita eius!'  
    }
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