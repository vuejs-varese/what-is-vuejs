---
transition: fade
---

# Hierarchy
Let's talk about Vue.js

<v-clicks>

- Composition over inheritance
- Parent - Child

</v-clicks>

---
layout: two-cols-header
transition: fade
---

# Hierarchy
Let's talk about Vue.js

::left::

- Composition over inheritance
- Parent - Child

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
- Parent - Child
- Props - Events

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

```vue {3,9,13,15,18|*}
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
- Parent - Child
- Props - Events
- Slots

::right::

> *`file://src/forms/CounterForm.vue`*

```vue
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

---
layout: two-cols-header
transition: fade
---

# Hierarchy
Let's talk about Vue.js

::left::

- Composition over inheritance
- Parent - Child
- Props - Events
- Slots

::right::

> *`file://src/views/ModalView.vue`*

```vue {*|2|3|8|10|9|*}
<script setup>
    defineProps({ title: String });
    defineEmits(["close"]);
</script>

<template>
    <div class="modal-view">
        <h2 v-if="title">{{ title }}</h2>
        <slot></slot>
        <button @click="$emit('close')">❌</button>
    </div>
</template>
```

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
- Parent - Child
- Props - Events
- Slots

::right::

> *`file://src/pages/ProfilePage.vue`*

```vue {*|4,5|7,8|13|14|15|16|*}
<script setup>
    import { ref } from "vue";

    import CounterForm from "../forms/CounterForm.vue";
    import ModalView from "../views/ModalView.vue";

    const isOpen = ref(false);
    const toggleModal = () => { isOpen.value = !isOpen.value; };
</script>

<template>
    <div id="profile-page">
        <ModalView v-show="isOpen"
                   title="Profile"
                   @close="toggleModal">
            <CounterForm />
        </ModalView>
        <!-- ... -->
    </div>
</template>
```

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
- Parent - Child
- Props - Events
- Slots
- Inject / Provide

::right::

> *`file://src/pages/HomePage.vue`*

```vue {*}
<script setup>
    import Carousel from "../components/Carousel.vue";
    import CarouselItem from "../components/CarouselItem.vue";
</script>

<template>
    <div id="home-page">
        <Carousel ...>
            <CarouselItem v-for="..." ... >
                <!-- ... -->
            </CarouselItem>
        </Carousel>
        <!-- ... -->
    </div>
</template>
```

::bottom::

<span style="color: transparent;">
    &nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />&nbsp;<br />
</span>
