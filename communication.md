---
layout: section
---
# Component communication
---
layout: default
---

# What are different ways to communicate?
- Using Props (Parent to Child Communication)
- Using Events (Child to Parent Communication)
- Using Event Bus (Communication between any components)
- Using provide/inject (Parent to Child Communication)
- Using this.$refs (Parent to Child Communication)

---
layout: default
---

# Props and events
- Props are used to pass data from parent to child with v-bind:propName="Value to be passed"
- In child they have to defned with defineProps, and accessed a "props.propName"
- Events are used to pass data from child to parent, using emit function, 
- They have to be defined by defineEmits in child.
- In parent they are catched by 'v-on:eventName' or '@eventName'


---
layout: two-cols
---

### Parent component code
```vue
<script setup>
import { ref } from 'vue';
import Child from './Child.vue';
const initialCount = 10;
const childCount = ref(initialCount);
const onChildCountChange = (newValue) => {
  childCount.value = newValue;
};
</script>
<template>
  <div>Child count in parent : {{ childCount }}</div>
  <Child
    class="mt-4"
    :initialCount="initialCount"
    :incrementBy="2"
    @onIncrement="onChildCountChange"
  />
</template>
```

::right::

### Child component code
```vue
<script setup>
import { ref } from 'vue';
const props = defineProps({
  initialCount: Number,
  incrementBy: Number,
});
const emit = defineEmits(['onIncrement']);
const count = ref(props.initialCount);
const increment = () => {
  count.value += props.incrementBy;
  emit('onIncrement', count.value);
};
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

### Output

<div class="bg-white p-2 text-black">
  <ComponentCommunication />
</div>

