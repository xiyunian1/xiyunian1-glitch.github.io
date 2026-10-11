<template>
  <section class="content-shell">
    <header class="page-hero">
      <div class="page-hero-copy">
        <p class="section-title">项目</p>
        <h1 class="page-heading">项目索引</h1>
        <p class="page-intro">
          两个围绕 AI 落地的项目。每篇文章记录它从第一版到现在的过程，附源码仓库和在线地址。
        </p>
      </div>
    </header>

    <div class="project-list">
      <article v-for="item in posts" :key="item.slug" class="simple-card">
        <RouterLink :to="`/posts/${item.slug}`" class="simple-card-title simple-card-stretch">{{ item.title }}</RouterLink>
        <p class="simple-card-desc">{{ item.summary }}</p>
        <div class="simple-card-meta">
          <span>{{ item.category }}</span>
          <span>{{ item.tags.map(tag => tag.name).slice(0, 4).join(' / ') }}</span>
        </div>
        <div v-if="item.repo || item.demo" class="simple-card-links">
          <a v-if="item.repo" class="text-link" :href="item.repo" target="_blank" rel="noreferrer">GitHub 源码</a>
          <a v-if="item.demo" class="text-link" :href="item.demo" target="_blank" rel="noreferrer">在线体验</a>
        </div>
      </article>
    </div>
  </section>
</template>

<script setup>
import { onMounted } from 'vue'
import { posts } from '../lib/posts'
import { setPageTitle } from '../lib/page'

onMounted(() => {
  setPageTitle('项目索引')
})
</script>
