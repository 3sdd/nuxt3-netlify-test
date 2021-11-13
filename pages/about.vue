<template>
    <div>
        <h1>about</h1>

        <div>
            data:{{data}}
        </div>
        <div>
            state:{{state}}
        </div>
        
        <!-- <Suspense>
            <template #default>
                aaa{{data}}
            </template>
            <template #fallback>
                loading
            </template>
        </Suspense> -->
    </div>
</template>

<script setup>
import axios from "axios"


const sleep = msec => new Promise(resolve => setTimeout(resolve, msec));

const data=ref(null)
let state=ref(false)
const asyncData=useAsyncData("count",async ()=>{
    const d=await $fetch("/api/count")
    await sleep(10000)
    console.log("done")
    state.value=true
    data.value=d
    return data
},{server:false})
console.log(asyncData)


</script>

