<template>
<div>
    <div>
        <img :src="mountain.image" alt="mountain.title" />
        <h4 class="title">{{ mountain.title }}</h4>
        <h4>Located in: </h4>
    
            <p v-for="country in mountain.countries">{{ country }}</p>
     
        <p class="subtitle">{{ mountain.description }}</p>
    </div>
    <NuxtLink  to="/">Back</NuxtLink>
</div>

</template>

<script>

export default {
    // asyncData is a hook that gets called before the page is loaded
    // fetch gets called after the page is loaded
    async asyncData({ params }) {
        const mountain = await fetch(
            `https://api.nuxtjs.dev/mountains/${params.slug}`
        ).then((res) => res.json())
        return { mountain }
    }
}
</script>
