<script setup lang="ts">
import type {Member} from "@/interfaces"

interface Props {
    id: number
}

const props = defineProps<Props>()
const memberList = useState<Map<number, Member>>("memberList")
const member = memberList.value.get(props.id) as Member

const localNote = computed(():string => {
    let localNote = member.note
    if(localNote == undefined){
        localNote = "--"
    }
    return localNote
})

const pointUp = ():void => {
    member.points++
}
</script>

<template>
    <section class="box">
        <h4>Information of {{ member.name }}</h4>
        <dl>
            <dt>ID</dt>
            <dt>{{ id }}</dt>
            <dt>mail address</dt>
            <dt>{{ member.email }}</dt>
            <dt>points</dt>
            <dt>{{ member.points }}</dt>            
            <dt>Note</dt>
            <dt>{{ localNote }}</dt>
        </dl>
        <button v-on:click="pointUp">Add point</button>
    </section>
</template>

<style scoped>
.box{
    border: green 1px solid;
    margin: 10px;
}
</style>