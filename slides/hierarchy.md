---
transition: fade
---

# Hierarchy
Let's talk about Vue.js

<v-clicks>

- Composition over inheritance
- Parent / Child

</v-clicks>

---
layout: two-cols-header
transition: fade
---

# Hierarchy
Let's talk about Vue.js

::left::

- Composition over inheritance
- Parent / Child

::right::

> *`file://src/forms/CounterForm.vue`*

````md magic-move

```vue {*|2}
<template>
    <form @submit.prevent="onSubmit">
        <!-- ... -->
    </form>
</template>

<script setup>
    /* ... */
</script>
```

```vue {2-5,9}
<template>
    <form @submit.prevent="onSubmit">
        <ClickCounter />
        <button type="submit">Submit</button>
    </form>
</template>

<script setup>
    import ClickCounter from "../components/ClickCounter.vue";

    /* ... */
</script>
```

```vue {11-16|*}
<template>
    <form @submit.prevent="onSubmit">
        <ClickCounter />
        <button type="submit">Submit</button>
    </form>
</template>

<script setup>
    import ClickCounter from "../components/ClickCounter.vue";

    const onSubmit = () => fetch("/api/submit", {
        method: "POST",
        body: JSON.stringify({ count: [...] })
    });
</script>
```

````

::bottom::

<span style="color: transparent;">
    &nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />
</span>

---
layout: two-cols-header
transition: fade
---

# Hierarchy
Let's talk about Vue.js

::left::

- Composition over inheritance
- Parent / Child
- Props / Events

::right::

> *`file://src/forms/CounterForm.vue`*

````md magic-move

```vue {*}
<template>
    <form @submit.prevent="onSubmit">
        <ClickCounter />
        <button type="submit">Submit</button>
    </form>
</template>

<script setup>
    import ClickCounter from "../components/ClickCounter.vue";

    const onSubmit = () => fetch("/api/submit", {
        method: "POST",
        body: JSON.stringify({ count: [...] })
    });
</script>
```

```vue {3,9,12,13,16}
<template>
    <form @submit.prevent="onSubmit">
        <ClickCounter :default="count" @change="onChange" />
        <button type="submit">Submit</button>
    </form>
</template>

<script setup>
    import { ref } from "vue";
    import ClickCounter from "../components/ClickCounter.vue";

    const count = ref(0);
    const onChange = (newValue) => { count.value = newValue; };
    const onSubmit = () => fetch("/api/submit", {
        method: "POST",
        body: JSON.stringify({ count: count.value })
    });
</script>
```

```vue {3|*}
<template>
    <form @submit.prevent="onSubmit">
        <ClickCounter v-model="count" />
        <button type="submit">Submit</button>
    </form>
</template>

<script setup>
    import { ref } from "vue";
    import ClickCounter from "../components/ClickCounter.vue";

    const count = ref(0);
    const onSubmit = () => fetch("/api/submit", {
        method: "POST",
        body: JSON.stringify({ count: count.value })
    });
</script>
```

````

::bottom::

<span style="color: transparent;">
    &nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />
</span>

---
transition: fade
---

# Hierarchy
Let's talk about Vue.js

- Composition over inheritance
- Parent / Child
- Props / Events
- Inject / Provide

<v-clicks>

- Slots
- Teleport

</v-clicks>
