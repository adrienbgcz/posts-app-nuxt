<template>
  <div>
    <div>Liste des posts</div>

    <div v-for="post in postsList" :key="post.id">
      <h1>{{post.title}}</h1>
      <p>{{post.body}}</p>
      <button><nuxt-link :to="`/posts/${post.id}`">Ouvrir</nuxt-link></button>

    </div>
  </div>
</template>

<script>


export default {
  name: "index",
  async asyncData({$axios}) {
    const postsList = await $axios.$get('https://jsonplaceholder.typicode.com/posts')
    return { postsList } // entre accolade car dans les data de vue, data est une fonction qui return un objet
  }
}
</script>

<style scoped>

</style>
