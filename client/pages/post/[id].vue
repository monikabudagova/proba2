<template>
    <!-- хлебные крошки -->
    <nav>
        <ul>
            <li><NuxtLink to="/blog">Блог</NuxtLink></li>
            <li><NuxtLink :style="'background-color:'+post.gategories[0].bg" :to="'/category/' + post.gategories[0].documentId">{{ post.gategories[0].title }}</NuxtLink></li>
            <li><strong>{{ post.title }}</strong></li>
        </ul>
    </nav>
    <!-- тело статьи -->
    <main>
        <h1>{{ post.title }}</h1>
        <p class="data">Дата публикации <span>{{ post.publishedAP }}</span></p>
        <img :src=base_url+post.img.url :alt=post.img.alternativeText>
        <div v-html="mark"></div>
    </main>
</template>

<style scoped>

    nav{
        padding: 30px;
        border-radius: 24px;
    }
    .data{
        display: flex;
        align-items: start;
        gap: 20px;
    }
    .data span{
        display: inline-block;
        text-wrap: nowrap;
        width: 112px;
        overflow: hidden;
    }
    main{
        padding: 40px;
        font-size: 24px;
    }
    li::before {
        content: ">>";
        margin-right: 10px;
    }
    li:first-child::before {
        display: none;
    }

    img {
        width: 765px;
    }
    nav ul{
        list-style: none;
        display: flex;
        gap: 10px;
    }
</style>

<script setup>
import MarkdownIt from "markdown-it";
const markdown = new MarkdownIt();



const { id } = useRoute().params

const api = await $fetch(`http://localhost:1337/api/posts/${id}?populate=*`);
const post = api.data;
const mark = markdown.render(post.body);

const base_url = 'http://localhost:1337'

const apiConfig = await $fetch(`${base_url}/api/config?populate=*`)
const config = apiConfig.data
useHead({
    title: `${post.title} - ${config.title}`
})
</script>