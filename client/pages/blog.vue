<template>
  <h2>Блог</h2>

  <main>
      <article v-for="(post, index) in posts" :key="post.id">
        <h3>{{ post.title }}</h3>
        <img :src="base_url + post.img.url" :alt=post.img.alternativeText>
        <p>{{ post.desc }}</p>
        <NuxtLink :to="'/post/' + post.documentId">˚˖𓍢ִ໋🦢˚</NuxtLink>
      </article>
  </main>

</template>

<script setup>
const api = await $fetch('http://localhost:1337/api/posts?populate=*')
const posts = api.data

const base_url = "http://localhost:1337"
</script>

<style scoped>

h2, main{
  color: #CD4662;
  font-weight: bold;
  display: flex;
  justify-content: center;
}
main {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  grid-auto-rows: minmax(100px, auto);
  grid-template-rows: repeat(4, 1fr);
  gap: 40px;
  padding: 40px;
}

@media (max-width: 1024px) {
  main {
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  }
}

@media (max-width: 768px) {
  main {
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  }
}

@media (max-width: 640px) {
  main {
    grid-template-columns: 1fr;
  }
}

article {
  background-color: #AEC289;
  padding: 10px;
  border-radius: 10px;
  height: max-content;
}

article img {
  border-radius: 10px;
  width: 100%;
  height: 150px;
  object-fit: cover;
}

article h3 {
  height: 70px;
}

article p {
  height: 56px;
}

article p,
article h3 {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-wrap: wrap;
}
</style>

