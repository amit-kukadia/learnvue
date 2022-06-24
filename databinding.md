---
layout: section
---
# Reactive data
---
layout: two-cols
---

# How to make reactive data?

We can create reactive data in two ways 
- Using reactive() function
- and ref() function

reactive() only takes objects, NOT JS primitives (String, Boolean, Number, BigInt, Symbol, null, undefined), however    
ref() can be used for primitives and objects

ref() takes the argument and returns it wrapped within a ref object with a .value property

eg. count.value

For the most parts we will be using ref.

::right::
### Code

```ts
<script setup>
import { ref, reactive } from 'vue';

const count = ref(0);

const state = reactive({ count: 0 })
</script>

<template>
  <button @click="count++">
    Count is: {{ count }}
  </button>
  <br>
  <button @click="state.count++">
    Count is: {{ state.count }}
  </button>
</template>

```

### Output

<div class="bg-white p-2 text-black">
  <ReactiveCounter />
</div>

---
layout: two-cols
---

# Text interpolation

- Using the "Mustache" syntax (double curly braces)
- Mustache tag will be replaced with the value of the property from the corresponding component instance. 
- It will also be updated whenever the property changes.

::right::
### Code

```vue
<script setup>
import { ref } from 'vue';
const name = ref('Amit');
const profession = 'Software developer';
const age = ref(20);
age.value++;
const increment = () => age.value++;
</script>

<template>
  <p>{{ name }} - {{ profession }} - {{ age }}</p>
  <br />
  <input v-model="name" class="w-24 mr-2" />
  <button @click="increment">Increment age</button>
</template>
```

### Output

<div class="bg-white p-2 text-black">
  <TextInterpolation />
</div>

---
layout: two-cols
---

# Raw HTML

- The double mustaches interprets the data as plain text, not HTML
- In order to output real HTML, you will need to use the v-html directive
- Dynamically rendering arbitrary HTML on your website can be very dangerous because it can easily lead to XSS vulnerabilities. Only use v-html on trusted content and never on user-provided content.

::right::
### Code

```js
<script setup>
import { ref } from 'vue';
const rawHtml = "<span style='color: red'>This should be red.</span>";
</script>

<template>
  <p>Using text interpolation: {{ rawHtml }}</p>
  <p>Using v-html directive: <span v-html="rawHtml"></span></p>
</template>
```

### Output

<div class="bg-white p-2 text-black">
  <HtmlTextInterpolation />
</div>
