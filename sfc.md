---
layout: section
---
# Single file components, aka "SFC's"
---
layout: two-cols
---

# What is SFC?

A Vue SFC encapsulates the 
- Component's logic (JavaScript)
- Template (HTML) 
- Styles (CSS) in a single file.

Vue components can be authored in two different API styles: 
- Options API 
- Composition API.

Over the course of these sessions we will be using Composion API as it is the recommended way.

::right::
### Code

```vue
<script setup>
import { ref } from 'vue';

const count = ref(0);
</script>

<template>
  <button @click="count++">Count is: {{ count }}</button>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>

```

### Output
<br>
<div class="bg-white p-2 text-black">
  <Counter :count="10"  />
</div>

---
layout: two-cols
---

# Options api variant

- It was the only way till vue 2
- The Composion api was introduced in version 3
- It provides better code reusability, and hence it is the way.

::right::
### Code

```vue
<script>
export default {
  data() {
    return {
      count: 0
    }
  }
}
</script>

<template>
  <button @click="count++">Count is: {{ count }}</button>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>
```
