<script lang="ts" setup>
    import { ref } from "vue";

    const props = defineProps({
        count: {
            default: 0,
            type: Number
        }
    });

    const counter = ref(props.count);
</script>

<template>
    <div flex="~"
         w="min"
         border="~ main rounded-md">
        <button border="r main"
                p="2"
                font="mono"
                outline="!none"
                hover:bg="gray-400 opacity-20"
                @click="counter -= 1">
            ➖
        </button>
        <span m="auto" p="2">{{ counter }}</span>
        <button border="l main"
                p="2"
                font="mono"
                outline="!none"
                hover:bg="gray-400 opacity-20"
                @click="counter += 1">
            ➕
        </button>
    </div>
</template>

<style scoped>
    button, span
    {
        min-width: 42.5px;
        text-align: center;
    }
</style>
