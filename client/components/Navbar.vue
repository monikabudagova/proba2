<template>
    <nav>
        <ul>
            <li><NuxtLink to="/">Главная</NuxtLink></li>
            <li><NuxtLink to="/blog">Блог</NuxtLink></li>
            <li><NuxtLink to="/contact">Контакты</NuxtLink></li>
        </ul>
        
    </nav>
</template>

<style scoped>
    ul {
        background-color: #F4DBDB;
        height: 50px;
        width: max;
        justify-content: space-evenly;

        font-weight: bold;


        list-style: none;
        display: flex;
        gap: 10px;
        padding: 0;
    }
    li{
        text-decoration: none;
    }
</style>