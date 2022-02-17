<template>
  <div>
    <h1>{{ title }}</h1>
    <p>{{ body }}</p>
    <div v-for="comment in comments">
      <h2>{{comment.name}}</h2>
      <p>{{comment.body}}</p>
      <p>{{comment.email}}</p>
    </div>


  </div>
</template>

<script>
export default {
  async asyncData({params, $axios}) { // créé la page côté serveur pour le renvoyer au client, expose le contexte contrairement au mounted, pas besoin d'import pour utiliser axios (voir nuxt context pour voir tout ce à quoi on a acces dans async data
    const slug = params.slug

    const {title, body} = await $axios.$get(`https://jsonplaceholder.typicode.com/posts/${slug}`)

    const comments = await $axios.$get(`https://jsonplaceholder.typicode.com/posts/${slug}/comments`)

    return {title, body, comments}
  },
}
</script>

<style scoped>

</style>
