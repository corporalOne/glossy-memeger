<template>
    <div
        class="fixed top-0 left-0 flex w-64 h-full bg-gray-800 opacity-100"
        :class="[ model ? 'flex-1 flex-col' : 'hidden' ]"
    >
        <div class="flex flex-1 flex-col overflow-y-auto pt-5 pb-4">
            <nav class="flex-1 space-y-1 bg-gray-800 px-2" aria-label="Sidebar">
                <a
                    v-for="item in navigation"
                    :key="item.name"
                    :href="item.href"
                    :class="[item.current ? 'bg-gray-900 text-white' : 'text-gray-300 hover:bg-gray-700 hover:text-white', 'group flex items-center px-2 py-2 text-sm font-medium rounded-md']">
                    <component :is="item.icon" :class="[item.current ? 'text-gray-300' : 'text-gray-400 group-hover:text-gray-300', 'mr-3 flex-shrink-0 h-6 w-6']" aria-hidden="true" />
                    <span class="flex-1">{{ item.name }}</span>
                    <span v-if="item.count" :class="[item.current ? 'bg-gray-800' : 'bg-gray-900 group-hover:bg-gray-800', 'ml-3 inline-block py-0.5 px-3 text-xs font-medium rounded-full']">{{ item.count }}</span>
                </a>
            </nav>
        </div>
    </div>
</template>

<script setup lang="ts">
import { CalendarIcon, ChartBarIcon, FolderIcon, HomeIcon, InboxIcon, UsersIcon } from '@heroicons/vue/24/outline'

const model = defineModel<boolean>({ required: true })

const navigation = [
    { name: 'Dashboard', icon: HomeIcon, href: '#', current: true },
    { name: 'Team', icon: UsersIcon, href: '#', count: 3, current: false },
    { name: 'Projects', icon: FolderIcon, href: '#', count: 4, current: false },
    { name: 'Calendar', icon: CalendarIcon, href: '#', current: false },
    { name: 'Documents', icon: InboxIcon, href: '#', current: false },
    { name: 'Reports', icon: ChartBarIcon, href: '#', count: 12, current: false },
]
</script>
