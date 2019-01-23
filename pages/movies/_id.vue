<template>
  <div>
    <h1>{{ content.name }}</h1>
    <nuxt-link to="/">home</nuxt-link>
    <p>{{ content.summary }}</p>
    <ul>
      <li v-for="genre in content.genres" :key="genre.id">
        {{ genre.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ app, params }) {
    const content = await app.$umbraco.getById(params.id)
    return {
      content
    }
  },
  head () {
    return {
      title: this.content.name
    }
  }

}
</script>

