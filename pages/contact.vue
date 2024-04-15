<template>
  <div class="bg-[#1E2021] text-[#FBF0C6] w-[100%] min-h-[100vh] flex flex-col p-1 px-[10vw] md:px-[20vw] gap-8 mx-auto">

    <AppHeader />
    <div class="flex flex-col gap-4">
    <p class="font-bold text-2xl">
      Contact
      </p>

      <p class="text-[#FBF0C6] font-semibold text-xl">
        Email
      </p>
      <NuxtLink class="text-[#FFA8CE] underline underline-offset-2" to="mailto:example@gmail.com">example@gmail.com</NuxtLink>

      <p class="text-[#FBF0C6] font-semibold text-md">
        Other useful links:
      </p> 
      <NuxtLink class="text-[#FFA8CE]" to="https://github.com">
        • GitHub
      </NuxtLink>
      <NuxtLink class="text-[#FFA8CE]" to="https://discord.com">
        • Discord
      </NuxtLink>
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
