---
transition: fade
---

# Using a CDN
Let's see some code

> *`file://src/index.html`*

````md magic-move

```html {*}
<!DOCTYPE html>
<html>
<head>
    <!-- ... -->
</head>
<body>
    <!-- ... -->
</body>
</html>
```

```html {5}
<!DOCTYPE html>
<html>
<head>
    <!-- ... -->
    <script src="https://unpkg.com/vue"></script>
</head>
<body>
    <!-- ... -->
</body>
</html>
```

```html {9-11}
<!DOCTYPE html>
<html>
<head>
    <!-- ... -->
    <script src="https://unpkg.com/vue"></script>
</head>
<body>
    <!-- ... -->
    <div id="app">
        {{ message }}
    </div>
    <!-- ... -->
</body>
</html>
```

```html {13-17}
<!DOCTYPE html>
<html>
<head>
    <!-- ... -->
    <script src="https://unpkg.com/vue"></script>
</head>
<body>
    <!-- ... -->
    <div id="app">
        {{ message }}
    </div>
    <!-- ... -->
    <script>
        const app = Vue.createApp({
            data: () => ({ message: "Hello, Vue.js!" })
        });
    </script>
</body>
</html>
```

```html {17|*}
<!DOCTYPE html>
<html>
<head>
    <!-- ... -->
    <script src="https://unpkg.com/vue"></script>
</head>
<body>
    <!-- ... -->
    <div id="app">
        {{ message }}
    </div>
    <!-- ... -->
    <script>
        const app = Vue.createApp({
            data: () => ({ message: "Hello, Vue.js!" })
        });
        app.mount("#app");
    </script>
</body>
</html>
```

````
