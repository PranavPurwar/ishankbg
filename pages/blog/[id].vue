<template>
	<main>
    <div class="bg-[#1E2021] text-[#FBF0C6] w-[100%] min-h-[100vh] flex flex-col p-1 px-[20vw] gap-8 mx-auto">
      <AppHeader />

			<div
				class="font-sans px-2 md:px-4 py-2 md:py-4 text-[#FBF0C6] text-md md:text-xl antialiased"
				id="content"
			/>

    <p>
      Copyright © 2024 Ishan Jaiswal
    </p>
		</div>
	</main>
</template>

<script setup lang="ts">
import DOMPurify from "dompurify"
import { marked } from "marked"
import markedLinkifyIt from "marked-linkify-it"
import { markedHighlight } from "marked-highlight";
import hljs from 'highlight.js';
import { markedSmartypants } from "marked-smartypants";

const route = useRoute()
const id = route.params.id

marked.use(markedLinkifyIt())
marked.use(markedHighlight({
    langPrefix: 'hljs language-',
    highlight(code, lang, info) {
      const language = hljs.getLanguage(lang) ? lang : 'plaintext';
      return hljs.highlight(code, { language }).value;
    }
  }))
marked.use(markedSmartypants())

marked.use({
	renderer: {
		link: (
			href: string,
			title: string | null | undefined,
			text: string,
		) => {
			return `<a class="underline text-[#FFA8CE]" href="${href}" target="_blank" rel="noopener noreferrer">${title || text}</a>`
		},
		strong: (text: string) => {
			return `<span class="font-bold text-[#d6bf64] text-xl md:text-2xl subpixel-antialiased">${text}</span>`
		},
		text: (text: string) => {
			return `<span>${text}</span>`
		},
		heading(text: string, level: number, raw: string) {
			return `
			<br>
			<h1 class="text-xl md:text-${
				5 - level
			}xl font-bold text-[#d6bf64] mb-2 mt-4 underline decoration-gray-700 underline-offset-8 decoration-2">${raw}</h1>
			<br>
			`
		},
    br() {
      return "\n<br>"
    },
    listitem(text: string) {
      return `<li class="text-[#FBF0C6] text-md md:text-xl antialiased">- ${text}</li>`
    },
	},
})

onMounted(async () => {
	const content = document.getElementById("content")

  // read file contents from file system in path ~/blog/[id].md directly
  const post = await fetch(`/blog/${id}.md`).then((res) => res.text())


	if (content) {
		content.innerHTML = DOMPurify.sanitize(
			// @ts-ignore
			marked.parse(post.replace(/\\n/g, "\n")),
		)
	}
})
</script>

<style>

</style>