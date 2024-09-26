<template>
    <h2>блог</h2>
    <main>
        <article>
            {{ posts }}
        </article>
    </main>
</template>
<script>
    let api = await $fetch('https;//dummyjson.com/posts')
    const posts = api.data
</script>