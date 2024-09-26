<template>
    <header>
        <h2>Главная страница</h2>
    </header>
    <main>
        <article v-for="(post, index) in posts" :key="post.id">
            <h3>{{ post.title }}</h3>
            <img src="https://i.pinimg.com/originals/8e/57/85/8e578585b383dc11bc8753de50819d34.jpg" alt="Обложка статьи">
            <ul>
                <li v-for="tag  in post.tags" :key="tag.id">
                    {{ tag }}
                </li>
            </ul>
            <nuxt-link :to="'/post/' + (index + 1)">Подробнее</nuxt-link>
        </article>
    </main>
</template>
<style scoped>
    main {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 20px;
    }
    article {
        border-radius: 10px;
        background-color: brown;
        color: wheat;
        padding: 10px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    } 
    article h3 {
        height: -webkit-fill-available;
    }
    article img {
        width: 100%;
        height: 180px;
        object-fit: cover;
        border-radius: 5px;
    }
    article a {
        padding: 10px;
        background-color: wheat;
        color: brown;
        text-decoration: none;
        text-align: center;
        display: block;
        border-radius: 5px;
    }
</style>
<script setup>
  const dataTwice = await $fetch('https://dummyjson.com/posts')
  const posts = dataTwice.posts
</script>