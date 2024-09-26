<template>
    <nav>
        <ul>
            <li><nuxt-link to='/'>Главная</nuxt-link></li>
            <li><strong>{{ post.data.attributes.title }}</strong></li>
        </ul>
    </nav>
    <main>
        <div>
            <img :src=home_url+post.data.attributes.cover.data.attributes.url alt="Обложка статьи">
            <h1>{{ post.data.attributes.title }}</h1>
            <p>{{ post.data.attributes.body }}</p>
            <!-- <ul v-for="tag in  post.tags" :key="tag.id">
                <li>{{ tag }}</li>
            </ul> -->
        </div>
    </main>
</template>

<script setup>
    const { id } = useRoute().params
    const post = await $fetch(`http://localhost:1337/api/posts/${id}?populate=*`)

    const home_url = "http://localhost:1337"
</script>

<style scoped>
    nav ul {
        display: flex;
        gap: 10px;
        list-style: none;
        padding: 0;
    }

    nav li {
        display: flex;
        gap: 10px;
    }

    nav li:first-child::before {
        display: none;
    }

    nav li::before {
        content: "»";
    }

    img {
        width: 100%;
        height: 240px;
        object-fit: cover;
        border-radius: 10px;
    }
</style>