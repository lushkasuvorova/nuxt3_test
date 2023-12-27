<script setup lang="ts">
import type { QueryBuilderParams } from '@nuxt/content/dist/runtime/types'
const query: QueryBuilderParams = { path: '/' }
</script>
<style>
a {
  text-decoration: none;
}

.wrapper {
  display: flex;
}

.block {
  display: inline-block;
  margin: 2px;
}
</style>
<template>
  <div>
    Все посты<br>
  </div>
  <ContentList :query="query" v-slot="{ list }">
    <div v-for="article in list" :key="article._path">
      <a :href="article._path">
        <div class="wrapper">
          <div class="block">
            <img :src="article.img" class="img-fluid" height="100px" />
          </div>
          <div class="block">
            <h2>{{ article.title }}</h2>
            <p>{{ article.description }}</p>
          </div>
        </div>
      </a>
    </div>
  </ContentList>
</template>