<script setup lang="ts">
import type {Member} from "@/interfaces"

const memberList = useState<Map<number, Member>>("memberList")

const totalPoints = computed(():number => {
    let total = 0
    for(const member of memberList.value.values()){
        total += member.points
    }
    return total
})

</script>

<template>
    <section>
        <h1>Member list</h1>
        <p>Total points of whole members: {{ totalPoints }}</p>
        <OneMember
            v-for="id in memberList.keys()"
            v-bind:key="id"
            v-bind:id="id"
        />
    </section>
</template>

<style scoped>
section{
    border: orage 1px dashed;
    margin: 10px;
}
</style>