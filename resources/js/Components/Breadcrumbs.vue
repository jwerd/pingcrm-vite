<template>
    <nav class="flex" aria-label="Breadcrumb">
        <ol role="list" class="text-white bg-indigo-800 flex space-x-4 rounded-md bg-white w-full shadow">
            <li v-for="page in pages" :key="page.name" class="flex">
                <div class="flex items-center">
                    <svg v-if="page.current" class="h-full w-6 flex-shrink-0 text-gray-200" viewBox="0 0 24 44" preserveAspectRatio="none" fill="currentColor" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
                        <path d="M.293 0l22 22-22 22h1.414l22-22-22-22H.293z" />
                    </svg>
                    <a :href="page.href" class="ml-4 text-sm font-medium text-white hover:text-gray-100" :aria-current="page.current ? 'page' : undefined">{{ page.name }}</a>
                </div>
            </li>
        </ol>
    </nav>
</template>

<script setup>
import { HomeIcon } from '@heroicons/vue/20/solid'

const props = defineProps({
    previous: {
        type: String,
        required: true
    },
    previous_url: {
        type: String,
        required: true
    },
    active: {
        type: String,
        required: true
    }
})


const pages = [
    { name: props.previous, href: props.previous_url, current: false },
    { name: props.active, current: true },
]
</script>
