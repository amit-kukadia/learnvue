---
layout: section
---
# Computed properties and watchers
---
layout: two-cols
---

# What are computed properties?
- A computed property is a way to define a data property, which depends on another data property/properties
- If any of the dependent property changes, the value of the computed property is re-evaluated.
- Value of a computed property is cached, and recomputed only when a dependent property changes.
- However if a method is used, it is recomputed everytime we try to get the value and also on each re-render
- This can improve performance if the computation is expensive.

::right::

### Code
```vue
<script setup>
import { ref, computed } from 'vue';
const count1 = ref(5);
const count2 = ref(5);
const sum = computed(() => {
  return count1.value + count2.value;
});
</script>

<template>
  <div class="flex flex-col gap-2">
    <div @click="count1++">Increment count1: {{ count1 }}</div>
    <div @click="count2++">Increment count1: {{ count2 }}</div>
    <div>Sum is {{ sum }}</div>
  </div>
</template>
```

### Output

<div class="bg-white p-2 text-black">
  <ComputedExample />
</div>


---
layout: two-cols
---

# What are Watchers?
- We can use the watch function to trigger a callback whenever a piece of reactive state changes
- A computed property good when we only want a value from a the dependent property/properties
- But sometimes we want to do some acions on change of a property, like make an api call, change another property, sync with localstorage etc
- We can watch a reactive object, ref, computed property, or combination of them together

::right::

### Code
```vue
<script setup>
import { ref, watch } from 'vue';

const x = ref(0);

watch(x, (newX, oldX) => {
  console.log(`new x is ${newX}, old x is ${oldX}`);
  if (newX % 3 === 0) {
    alert(`${newX} is a multiple of 3`);
  }
});
</script>

<template>
  <button @click="x++">x is: {{ x }}</button>
</template>

```

### Output

<div class="bg-white p-2 text-black">
  <WatcherExample />
</div>