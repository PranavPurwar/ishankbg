<template>
  <div class="bg-[#1E2021] text-[#FBF0C6] w-[100%] min-h-[100vh] flex flex-col p-1 px-[10vw] md:px-[20vw] gap-8 mx-auto">

    <AppHeader />
    <div class="flex flex-col gap-4">
    <p class=" font-semibold text-2xl">
      Blog Articles
      </p>

      <p class="text-[#FBF0C6]">
        Some of my recent blog articles.
      </p>
    </div>

    <div class="flex flex-col gap-4">
      <h2 class="text-[#d6bf64] text-xl font-bold">
        Recent Articles
      </h2>

      <div class="flex flex-col gap-4">
        <div v-for="blog in BLOG_DATA">
          • {{ blog.date }} - 
          <NuxtLink class="text-[#FFA8CE]" :to="`/blog/${blog.slug}`">
            {{ blog.title }}
          </NuxtLink>
        </div>
      </div>
    </div>

    <div class="flex flex-wrap items-center justify-center text-center gap-4">
      <p v-for="skill in SKILLS" class="bg-[#3B3836] p-2 w-fit rounded-lg text-md">
        {{ skill }}
        </p>
    </div>

    <p>
      Copyright © 2024 Ishan Jaiswal
    </p>
  </div>
</template>

<script setup lang="ts">

import AppHeader from '../components/AppHeader.vue';
import { BLOG_DATA, LINKS, PROJECTS, SKILLS } from '../assets/css/data';
</script>
