<template>
  <div class="bg-[#1E2021] text-[#FBF0C6] w-[100%] min-h-[100vh] flex flex-col p-1 px-[20vw] gap-8 mx-auto">

    <AppHeader />
    <div class="flex flex-col gap-4">
    <p class="text-[#FFA8CE] text-3xl font-bold">
      Ishan Jaiswal
      </p>

      <p class="text-[#FBF0C6]">
        Tech Enthusiast | Addicted to Javascript
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


    <div class="flex flex-col gap-4">
      <h2 class="text-[#d6bf64] text-xl font-bold">
        Highlighted Projects
      </h2>

      <div class="flex flex-col gap-4">
        <div v-for="project in PROJECTS">
          • {{ project.title }} - 
          <NuxtLink class="text-[#FFA8CE]" :to="`/blog/${project.slug}`">
            {{ project.description }}
          </NuxtLink>
        </div>
      </div>
    </div>

    <div class="flex flex-col gap-4">
      <h2 class="text-[#d6bf64] text-xl font-bold">
        Quick Links
      </h2>

      <div class="flex flex-col gap-4">
        <div v-for="link in LINKS">
          • 
          <NuxtLink class="text-[#FFA8CE]" :to="`/blog/${link.url}`">
            {{ link.title }}
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

import AppHeader from './components/AppHeader.vue';
import { BLOG_DATA, LINKS, PROJECTS, SKILLS } from './assets/css/data';
</script>
