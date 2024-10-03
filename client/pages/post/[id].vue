<template>
     <!-- хлебные крошки-->
    <nav>
        <ul>
            <li><NuxtLink to="/blog">блог</NuxtLink></li>
            <!-- <li><NuxtLink :to="'/category/' + post.categories[0].id">{{ post.categories[0].title }}</NuxtLink></li> -->
            <li>{{ post.title }}</li>
        </ul>
    </nav>
         <!--  тело статьи-->
    <main>
        <h1>{{ post.title }}</h1>
        <img :src=base_url+post.img.url :alt=post.img.alternativeText>
        <div v-html="mark"></div>
    </main>
</template>

<script setup>
import MarkdownIt from "markdown-it";
const markdown = new MarkdownIt();

const { id } = useRoute().params

const api = await $fetch(`http://localhost:1337/api/categories?populate=*`)
const post = api.data[id]
const mark = markdown.render(post.body);

const base_url = 'http://localhost:1337'

</script>

<style>
li::before{
    content: ">>";
    margin-right: 10px;
    
}
img{
width: 765px;
}
nav ul {
list-style: none;

}
</style>