<template>
  <div>
    <h2 class="text-gray-500 text-xs font-medium uppercase tracking-wide">Recently Updated Guides</h2>
    <ul class="mt-3 grid grid-cols-1 gap-5 sm:gap-6 sm:grid-cols-2 lg:grid-cols-4">
      <li class="col-span-1 flex shadow-sm rounded-md">
        <div class="flex-shrink-0 flex items-center justify-center w-16 bg-pink-600 text-white text-sm leading-5 font-medium rounded-l-md">
          Ruby
        </div>
        <div class="flex-1 flex items-center justify-between border-t border-r border-b border-gray-200 bg-white rounded-r-md truncate">
          <div class="flex-1 px-4 py-2 text-sm leading-5 truncate">
            <NuxtLink to="/hello" class="text-gray-900 font-medium hover:text-gray-600 transition ease-in-out duration-150">Graph API</NuxtLink>
          </div>

        </div>
      </li>

      <li class="col-span-1 flex shadow-sm rounded-md">
        <div class="flex-shrink-0 flex items-center justify-center w-16 bg-purple-600 text-white text-sm leading-5 font-medium rounded-l-md">
          Vue
        </div>
        <div class="flex-1 flex items-center justify-between border-t border-r border-b border-gray-200 bg-white rounded-r-md truncate">
          <div class="flex-1 px-4 py-2 text-sm leading-5 truncate">
            <a href="#" class="text-gray-900 font-medium hover:text-gray-600 transition ease-in-out duration-150">Component Design</a>
            <p class="text-gray-500">12 Members</p>
          </div>
        </div>
      </li>

      <li class="col-span-1 flex shadow-sm rounded-md">
        <div class="flex-shrink-0 flex items-center justify-center w-16 bg-orange-500 text-white text-sm leading-5 font-medium rounded-l-md">
          Linux
        </div>
        <div class="flex-1 flex items-center justify-between border-t border-r border-b border-gray-200 bg-white rounded-r-md truncate">
          <div class="flex-1 px-4 py-2 text-sm leading-5 truncate">
            <a href="#" class="text-gray-900 font-medium hover:text-gray-600 transition ease-in-out duration-150">Templates</a>
            <p class="text-gray-500">16 Members</p>
          </div>
        </div>
      </li>

      <li class="col-span-1 flex shadow-sm rounded-md">
        <div class="flex-shrink-0 flex items-center justify-center w-16 bg-green-400 text-white text-sm leading-5 font-medium rounded-l-md">
          AWS
        </div>
        <div class="flex-1 flex items-center justify-between border-t border-r border-b border-gray-200 bg-white rounded-r-md truncate">
          <div class="flex-1 px-4 py-2 text-sm leading-5 truncate">
            <a href="#" class="text-gray-900 font-medium hover:text-gray-600 transition ease-in-out duration-150">React Components</a>
            <p class="text-gray-500">8 Members</p>
          </div>
        </div>
      </li>
    </ul>
    <br>
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
