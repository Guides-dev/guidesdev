<template>
  <div>
    <div>
    <h2 class="text-gray-500 text-xs font-medium uppercase tracking-wide">Recent Guides</h2>
    <ul>
      <li v-for="guide of guides" :key="guide.slug">
        <NuxtLink :to="{ name: 'slug', params: { slug: guide.slug } }">
          <div>
            <h2>{{ guide.title }}</h2>
          </div>
        </NuxtLink>
      </li>
    </ul>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  async asyncData({ $content, params }) {
    const guides = await $content(params.slug)
      .only(['title', 'description', 'slug'])
      .sortBy('createdAt', 'asc')
      .fetch()

    return {
      guides
    }
  }
})

</script>
