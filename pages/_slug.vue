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
