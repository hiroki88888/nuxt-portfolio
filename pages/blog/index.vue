// blog.vue

<template>
        <div>
            <h1>Blog</h1>
            <p>エンジニアの日常生活をお届けします</p>
                <div v-for="singleData in data" :key="singleData.id">
                    <div>
                        <h3>{{ singleData.title }}</h3>
                        <p>{{ singleData.excerpt }}</p>
                        <p>{{ singleData.date }}</p>
                            <NuxtLink :to="singleData._path">Read More</NuxtLink>
                    </div>
                    <div>
                        <img :src="singleData.image" alt="blog-image">
                    </div>
                </div>
        </div>
</template>

<script setup>
    const { data } = await useAsyncData("blogQuery",()=>queryContent("/blog").sort({ id: -1 }).find()
    )
</script>
