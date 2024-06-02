<h1>
    SFC
    <small>(Single File Component)</small>
</h1>

Let's see some code

> *`file://src/components/ClickCounter.vue`*

````md magic-move

```vue
<template>
    <!-- ... -->
</template>

<script setup>
    /* ... */
</script>

<style scoped>
    /* ... */
</style>
```

```vue {1-7}
<template>
    <div>
        <button class="minus" @click="count -= 1">➖</button>
        <span>{{ count }}</span>
        <button class="plus" @click="count += 1">➕</button>
    </div>
</template>

<script setup>
    /* ... */
</script>

<style scoped>
    /* ... */
</style>
```

```vue {9-13}
<template>
    <div>
        <button class="minus" @click="count -= 1">➖</button>
        <span>{{ count }}</span>
        <button class="plus" @click="count += 1">➕</button>
    </div>
</template>

<script setup>
    import { ref } from "vue";

    const count = ref(10);
</script>

<style scoped>
    /* ... */
</style>
```

```vue {15-19|*}

<template>
    <div>
        <button class="minus" @click="count -= 1">➖</button>
        <span>{{ count }}</span>
        <button class="plus" @click="count += 1">➕</button>
    </div>
</template>

<script setup>
    import { ref } from "vue";

    const count = ref(10);
</script>

<style scoped>
    .plus { background-color: green; }
    .minus { background-color: red; }
</style>
```

```vue {9,15}
<template>
    <div>
        <button class="minus" @click="count -= 1">➖</button>
        <span>{{ count }}</span>
        <button class="plus" @click="count += 1">➕</button>
    </div>
</template>

<script lang="ts" setup>
    import { ref } from "vue";

    const count = ref(10);
</script>

<style lang="scss" scoped>
    .plus { background-color: green; }
    .minus { background-color: red; }
</style>
```

````

