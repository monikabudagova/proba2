<template>
  <h2>Блог</h2>

  <main>
    <article v-for="(post, index) in posts" :key="post.id">
      <h3>{{ post.title }}</h3>
      <img :src=base_url+post.img.url :alt=post.img.alternativeText>
      <p>{{ post.desc }}</p>
      <NuxtLink :to="'/post/' + post.id">Подробнее</NuxtLink>
    </article>
  </main>

</template>

<script setup>
const api = await $fetch('http://localhost:1337/api/posts?populate=*')
const posts = api.data

const base_url = "http://localhost:1337"
</script>

<style scoped>
main {

  display: flex;
  gap: 10px;
}

article {
  background-color: #f5f5f5;
  padding: 10px;
  width: 300px;

  display: flex;
  flex-direction: column;

}
article{
background-color: #f5f5f5;

}

article img{
width: 100%;

}
article a{
display: block;

}

</style>

