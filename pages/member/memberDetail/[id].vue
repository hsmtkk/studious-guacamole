<script setup lang="ts">
import type {Member} from "@/interfaces"

const PAGE_TITLE = "Member info detail"

definePageMeta({
    layout: "member"
})

useHead({
    title: PAGE_TITLE
})

const route = useRoute()
const memberList = useState<Map<number, Member>>("memberList")

const member = computed(():Member => {
    const id = Number(route.params.id)
    return memberList.value.get(id) as Member
})

const localNote = computed(():string => {
    let localNote = "--"
    if(member.value.note != undefined){
        localNote = member.value.note
    }
    return localNote
})
</script>

<template>
    <nav id="breadcrumbs">
        <ul>
            <li><NuxtLink v-bind:to="{name: 'index'}">TOP</NuxtLink></li>
            <li><NuxtLink v-bind:to="{name: 'member-memberList'}">Member list</NuxtLink></li>
            <li>{{ PAGE_TITLE }}</li>
        </ul>
    </nav>
    <section>
        <h2>{{ PAGE_TITLE }}</h2>
        <dl>
            <dt>ID</dt>
            <dd>{{ member.id }}</dd>
            <dt>Name</dt>
            <dd>{{ member.name }}</dd>
            <dt>Mail address</dt>
            <dd>{{ member.email }}</dd>
            <dt>Points</dt>
            <dd>{{ member.points }}</dd>
            <dt>Note</dt>
            <dd>{{ localNote }}</dd>

        </dl>
    </section>
</template>
