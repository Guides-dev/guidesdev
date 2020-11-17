<template>
  <article>
    <h1>{{ doc.title }}</h1>
    <nuxt-content :document="doc" />
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const doc = await $content(params.slug || 'index').fetch()

    return { doc }
  }
}
</script>

<style>
h1 {
  font-weight: bold;
  font-size: 28px;
}
.nuxt-content h2 {
  font-weight: bold;
  font-size: 22px;
}
.nuxt-content h3 {
  font-weight: bold;
  font-size: 16px;
}
.nuxt-content p {
  margin-bottom: 20px;
}
</style>
