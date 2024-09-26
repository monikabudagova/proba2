<template>
    <nav>
        <ul>
            <li><nuxt-link to="/">Home</nuxt-link></li>
            <li><nuxt-link to="/about">About</nuxt-link></li>
            <li><nuxt-link to="/contact">Contact</nuxt-link></li>
        </ul>

    </nav>
</template>

<style scoped>


ul {
    display: flex;
    list-style: none;
    gap: 10px;
    padding: 0;
}

li {
    margin: 0;
    
}

a {
    text-decoration: none;
    background-color: brown;
    color: wheat;
    padding: 10px;
    font-size: 24px;
}

li:first-child a {
    border-radius: 10px 0 0 10px;
}

li:last-child a {
    border-radius: 0 10px 10px 0;
}

a:hover {
    background-color: wheat;
    color: brown;
}
</style>