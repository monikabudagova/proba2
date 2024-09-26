<template>
    <h2>блог</h2>

    <main>
        <article v-for="post in posts" :key="post.id">
            <h3>{{ posts.title }}</h3>
            <img :src=base_url+post.img.url alt="обложка статьи">
            <p>{{ post.desc }}</p>
            <NuxtLink to="#">подробнее</NuxtLink>
        </article>
    </main>
</template>
<script>
    const api = await $fetch('https;//dummyjson.com/posts')
    const posts = api.data

    const base_url = 'http://localhost:1337'
</script>
<style scoped>
main{
    display: flex;
    gap: 10px;
}

</style>