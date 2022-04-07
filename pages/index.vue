<template>
  <div>
    <p v-if="$fetchState.pending">Fetching mountains...</p>
    <p v-else-if="$fetchState.error">An error occurred :(</p>
    <div v-else>
      <h1>Nuxt Mountains</h1>
      <ul>
        <li v-for="mountain of mountains">
          <NuxtLink :to="mountain.slug" :key="mountain.title">
            {{mountain.title}}
          </NuxtLink>
        </li>
      </ul>
      <button @click="$fetch">Refresh</button>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        mountains: []
      }
    },
    async fetch() {
      this.mountains = await fetch(
        'https://api.nuxtjs.dev/mountains'
      ).then(res => res.json())
    }
  }
</script>

<style scoped>
.links {
  display: flex;
  flex-direction: column;
  padding-top: 15px;
}
ul {
  list-style: none;
  display: flex;
  flex-direction: row;
  margin-bottom: 40px;
  text-align: center;
  justify-content: center;
}
li {
  padding: 0 20px;
}
svg {
  padding-right: 20px;
}
img {
  height: 120px;
}
</style>
