<script setup lang="ts">
import type {Member} from "@/interfaces"

const PAGE_TITLE = "Add member info"

definePageMeta({
    layout: "member"
})

useHead({
    title: PAGE_TITLE
})

const router = useRouter()
const memberList = useState<Map<number, Member>>("memberList")

const member: Member = reactive({
    id: 0,
    name: "",
    email: "",
    points: 0,
    note: "",
})

const onAdd = ():void => {
    memberList.value.set(member.id, member)
    router.push({name: "member-memberList"})
}

</script>

<template>
    <h1>Member management</h1>
    <nav id="breadcrumbs">
        <ul>
            <li><NuxtLink v-bind:to="{name: 'index'}">TOP</NuxtLink></li>
            <li><NuxtLink v-bind:to="{name: 'member-memberList'}">Member list</NuxtLink></li>
            <li>{{ PAGE_TITLE }}</li>
        </ul>
    </nav>
    <section>
        <h2>{{ PAGE_TITLE }}</h2>
        <p>
            Input member information and press entry button.
        </p>
        <form v-on:submit.prevent="onAdd">
            <dl>
                <dt><label for="addId">ID</label></dt>
                <dd><input type="number" id="addId" v-model.number="member.id" required></dd>
                <dt><label for="addName">Name</label></dt>
                <dd><input type="text" id="addName" v-model="member.name" required></dd>
                <dt><label for="addEmail">Mailaddress</label></dt>
                <dd><input type="email" id="addEmail" v-model="member.email" required></dd>
                <dt><label for="addPoints">Points</label></dt>
                <dd><input type="number" id="addPoints" v-model.number="member.points" required></dd>
                <dt><label for="addNote">Note</label></dt>
                <dd><textarea id="addNote" v-model="member.note"></textarea></dd>
            </dl>
            <button type="submit">Entry</button>
        </form>
    </section>
</template>
