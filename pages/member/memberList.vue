<script setup lang="ts">
import type {Member} from "@/interfaces"

const PAGE_TITLE = "Member list"

definePageMeta({
    layout: "member"
})

useHead({
    title: PAGE_TITLE
})

const memberList = useState<Map<number, Member>>("memberList")
</script>

<template>
    <nav id="breadcrumbs">
        <ul>
            <li><NuxtLink v-bind:to="{name: 'index'}">TOP</NuxtLink></li>
            <li>Member list</li>
        </ul>
    </nav>
    <section>
        <h2>Member list</h2>
        <p>
            <NuxtLink v-bind:to="{name: 'member-memberAdd'}">New member entry</NuxtLink>
        </p>
        <section>
            <ul>
                <li
                v-for="[id,member] in memberList"
                v-bind:key="id"
                >
                <NuxtLink v-bind:to="{name: 'member-memberDetail-id', params:{id: id}}">ID {{ id }} {{ member.name }}</NuxtLink></li>
            </ul>
        </section>
    </section>
</template>
