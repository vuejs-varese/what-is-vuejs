---
layout: two-cols-header
transition: fade
---

<h1>
    SFC
    <small>(Single File Component)</small>
</h1>

Let's see some code

::left::

> *`file://src/components/ClickCounter.vue`*

```vue
<template>
    <div class="click-counter">
        <button @click="count -= 1">➖</button>
        <span>{{ count }}</span>
        <button @click="count += 1">➕</button>
    </div>
</template>

<script lang="ts" setup>
    import { ref } from "vue";

    const count = ref(10);
</script>

<style lang="scss" scoped>
    /* ... */
</style>
```

::right::

<div class="hv-centered">
    <div>
        <ClickCounter v-after :count="10" m="t-4" />
    </div>
</div>

<style>
    .hv-centered
    {
        align-items: center;
        display: flex;
        flex-direction: column;
        height: 100%;
        justify-content: center;
    }
</style>
