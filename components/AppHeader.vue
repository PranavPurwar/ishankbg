<template>
  <div class="flex bg-[#32302F] p-4 w-full rounded-lg mx-auto items-center justify-between">
    <div class="flex gap-4 items-center">
      <NuxtImg
        src="https://cdn.discordapp.com/avatars/662311430682443786/8be450cca181b565b29a2189d49c49c5.webp?size=240"
        class="rounded-lg" alt="Logo" width="50" height="50" />
      <NuxtLink to="/" class="text-lg font-bold">IshanKBG</NuxtLink>
    </div>

    <div class="hidden md:flex gap-4">
      <NuxtLink to="/blog" class="text-[#FBF0C6]">Blog</NuxtLink>
      <NuxtLink to="/contact" class="text-[#FBF0C6]">Contact</NuxtLink>
      <NuxtLink to="/" class="text-[#FBF0C6]">Resume</NuxtLink>
      <NuxtLink to="/" class="text-[#FBF0C6]">Talks</NuxtLink>
    </div>

    <Sheet>
      <SheetTrigger class="lg:hidden">
        <img class="h-8 w-8 invert" src="/svg/menu.svg" alt="Menu" />
      </SheetTrigger>

      <SheetContent class="bg-[#1E2021] p-8 flex flex-col rounded-s-3xl">

        <SheetHeader class="text-gray-200">
          <SheetTitle class="text-2xl font-semibold text-[#d6bf64]">Menu</SheetTitle>
        </SheetHeader>

        <div class="flex flex-col gap-4 py-2 font-semibold text-xl underline underline-offset-4">
          <NuxtLink to="/blog" class="text-[#FBF0C6]">Blog</NuxtLink>
          <NuxtLink to="/contact" class="text-[#FBF0C6]">Contact</NuxtLink>
          <NuxtLink to="/" class="text-[#FBF0C6]">Resume</NuxtLink>
          <NuxtLink to="/" class="text-[#FBF0C6]">Talks</NuxtLink>
        </div>


        <p class="bottom-8 fixed text-md text-[#d6bf64]">
          Copyright © 2024 Ishan Jaiswal
        </p>
      </SheetContent>
    </Sheet>

  </div>
</template>

<script lang="ts" setup>

import { Sheet, SheetContent, SheetTrigger } from './ui/sheet'

</script>

<style></style>