<template>
    <div>
        <h1>VUE3.0生命周期函数</h1>
        <span>{{ count }} </span>
        <ul>
            <li v-for="item in state.list" :key="item.id">
                {{ item.name }}
            </li>
        </ul>
    </div>
</template>
<script lang="ts">
import {
    onActivated,
    onBeforeMount,
    onMounted,
    onBeforeUnmount,
    onBeforeUpdate,
    onDeactivated,
    onErrorCaptured,
    onRenderTracked,
    onRenderTriggered,
    onUnmounted,
    onUpdated,
    ref,
    reactive,
} from 'vue'

export default {
    setup(props, context) {
        const state = reactive({
            list: [
                { name: 'well1', id: 1, age: 10 },
                { name: 'well2', id: 2, age: 11 },
                { name: 'well3', id: 3, age: 12 },
                { name: 'well4', id: 4, age: 13 },
            ],
        })
        // 使用ref 定义值时，取值或者改变值 对应.value
        const count = ref(1)
        console.log('beforeCreated和created废弃了，直接setup即可')

        onErrorCaptured(() => {
            console.log('onErrorCaptured-错误时候执行）')
        })
        onRenderTracked(() => {
            console.log('onRenderTracked - 新增')
        })
        onRenderTriggered(e => {
            console.log(e)
            console.log('onRenderTriggered - 新增 - 检查哪个依赖性导致组件重新渲染')
        })
        onBeforeMount(() => {
            console.log('onBeforeMount')
        })
        onMounted(() => {
            console.log('onMounted')
        })
        onUnmounted(() => {
            console.log('onUnmounted - 对应vue2的destroyed')
        })
        onBeforeUnmount(() => {
            console.log('onBeforeUnmount - 对应vue2的beforeDestroyed')
        })
        onBeforeUpdate(() => {
            console.log('onBeforeUpdate')
        })
        onUpdated(() => {
            console.log('onUpdated')
        })


        onActivated(() => {
            console.log('onActivated')
        })

        // setInterval(() => {
        //     count.value++
        // }, 2000)
        return {
            count,
            state,
        }
    },
}
</script>
