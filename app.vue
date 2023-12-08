<script setup lang="ts">
import type {Member} from "@/interfaces"

const SITE_TITLE = "Sample to change header"

useHead({
  titleTemplate: (titleChunk: string|undefined):string => {
    let title = SITE_TITLE
    if(titleChunk != undefined){
      title = `${titleChunk} | ${SITE_TITLE}`
    }
    return title
  }
})

useState<Map<number, Member>>("memberList", (): Map<number, Member> => {
  const memberListInit = new Map<number, Member>();
  memberListInit.set(33456, {id:3346, name:"Tanaka Taro", email:"taro@example.com", points:10, note:"Hoge"})
  memberListInit.set(44567, {id:44567, name:"Suzuki Jiro", email:"jiro@example.com", points:20})
  return memberListInit
})


</script>

<template>
  <NuxtLayout>
    <NuxtPage/>
  </NuxtLayout>
</template>

<style>
main{
  border: blue 1px solid;
  padding: 10px;
}

#breadcrumbs ul li{
  display: inline;
  list-style-type: none;
}

#breadcrumbs{
  margin-left: 0px;
}

#breadcrumbs ul{
  padding-left: 0px;
}

#breadcrumbs ul .current{
  color: red;
}

#breadcrumbs ul li:before{
  content: " > ";
}

#breadcrumbs ul li:first-child:before{
  content: none;
}
</style>