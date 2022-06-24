---
layout: section
---
# Vue Directives
---

# List of builtin directives
- ***v-text and v-html*** for text and html data respectively (use mustache syntax instead of v-text) 
- ***v-if, v-else and v-else-if*** for conditional rendering
- ***v-show*** toggles the element's visibility, by setting the display CSS property via inline styles
- ***v-for*** renders the element or template block multiple times based on the source data (array or object).
- ***v-on*** attaches an event listener to the element; shorthand '@'.
- ***v-bind*** dynamically binds one or more attributes, or a component prop to an expression; shorthand: ':'.
- ***v-model*** creates a two-way binding on a form input element or a component.
- ***v-slot*** denotes named slots or slots that expect to receive props; shorthand: '#'
- and some more...

---
layout: two-cols
---

# Conditional rendering

- v-if : It takes a value/expression and displays the element based on the truthy value.
- v-else : it is chained with the v-if directive, and is displayed if the truthy value of v-if is false.
- v-else-if:  serves as an "else if block" for v-if. It can also be chained multiple times.
- v-show: Same as v-if, only difference is that an element with v-show will always be rendered and remain in the DOM; v-show only toggles the display CSS property of the element.

::right::
### Code

```vue
<script setup>
import { ref } from 'vue';
const display = ref(false);
const toggle = () => (display.value = !display.value);
</script>
<template>
  <button @click="toggle" class="border">Toggle</button>
  <button @click="display = 'something else'" class="ml-4 border">
    Make it something else
  </button>
  <div v-if="display === true">display is true</div>
  <div v-else-if="display === false">display is false</div>
  <div v-else>display is something else</div>
  <div v-show="display">v-display is true</div>
</template>
```

### Output

<div class="bg-white p-2 text-black">
  <ConditionalRendering />
</div>

---
layout: two-cols
---

### List rendering with array

- We can use the v-for directive to render a list of items based on an array. 
- The v-for directive requires a special syntax in the form of item in items, where items is the source data array and item is an alias for the array element being iterated on.
- We can also get the index of the element as the second key

### Output
<div class="bg-white p-2 text-black mr-2">
  <ListRendering />
</div>

::right::
```vue
<script setup>
const products = [
  {
    productName: 'Phone',
    cost: 100,
  },
  {
    productName: 'TV',
    cost: 50,
  },
  {
    productName: 'Laptop',
    cost: 150,
  },
];
</script>
<template>
  <div
    v-for="(product,index) in products"
    class="my-2 border w-full p-2"
  >
    {{index}}. Name is {{ product.productName }} and cost is {{ product.cost }}
  </div>
</template>
```

---
layout: two-cols
---

### List rendering with Objects

- We can also use v-for to iterate through the properties of an object. 
- We can provide a second alias for the property's name (a.k.a. key).

### Output
<div class="bg-white p-2 text-black mr-2">
  <ObjectRendering />
</div>

::right::
### Code
```vue
<script setup>
const productDetail = {
  brand: 'Samsung',
  category: 'Televison',
  cost: 200,
  rating: 4,
};
</script>

<template>
  <div
    v-for="(value, key, index) in productDetail"
    :key="index"
    class="my-2 border w-full p-2"
  >
    {{ index + 1 }}. {{ key }} is {{ value }}
  </div>
</template>

```

---
layout: two-cols
---

# Event Handling

We use the v-on directive, which we typically shorten to the @ symbol, to listen to DOM events and run some JavaScript when they're triggered. 
The usage would be v-on:click="handler" or with the shortcut, @click="handler".

The handler value can be one of the following:

- Inline handlers: Inline JavaScript to be executed when the event is triggered (similar to the native onclick attribute).

- Method handlers: A property name or path that points to a method defined on the component.


::right::
### Code
```vue
<script setup>
import { ref } from 'vue';
const onClick = () => {
  alert('function call clicked');
};

const count = ref(0);
</script>

<template>
  <div v-on:mouseover="count++">Mouse over count: {{ count }}</div>
  <div class="mt-4" @click="onClick">function call clicked</div>
</template>

```

### Output

<div class="bg-white p-2 text-black">
  <ClickHandler />
</div>


---
layout: two-cols
---

# Event data

- We can get the data from the element that is clicked, by passing it to the function.
- We can also access the native event data, by accessing the $event

### Output

<div class="bg-white p-2 text-black mr-2">
  <EventData />
</div>

::right::

### Code
```vue
<script setup>
const products = [
  {
    productName: 'Phone',
    cost: 100,
  },
  {
    productName: 'TV',
    cost: 50,
  },
];
const logProduct = (event, product) => console.log(event, product.productName);
</script>
<template>
  <div
    v-for="(product, index) in products"
    :key="product.productName"
    class="my-2 border w-full p-2"
    @click="logProduct($event, product)"
  >
    {{ index }}. Name is {{ product.productName }} and cost is
    {{ product.cost }}
  </div>
</template>
```

---
layout: two-cols
---

# Data binding with v-bind

- It is used to pass a dynamic attribute to an html element or a prop to custom component
- It has a shorthand syntax, by using ':'
- eg. dynamic image src for img tag; dynamic classes; styles etc


::right::

### Code

```vue
<script setup>
import { ref } from 'vue';
const isDisabled = ref(false);
const name = ref('John');
const toggle = () => (isDisabled.value = !isDisabled.value);
</script>

<template>
  <p>{{ name }}</p>
  <input
    v-model="name"
    :disabled="isDisabled"
    class="w-24 mr-2 border-3 border-black"
  />
  <button @click="toggle">Toggle</button>
</template>
```

### Output

<div class="bg-white p-2 text-black mr-2">
  <DynamicAttribute />
</div>

---
layout: two-cols
---

# Two way data binding

- v-model directive is used to create a two-way binding on a form input element or a component.
- It can be used to input, select and textarea html elements
- Custom components can also have v-model
- It is a short hand for handling the event and updating the value

::right::

### Code

```vue
<script setup>
import { ref } from 'vue';
const text = ref('John');
</script>
<template>
  <div>
    {{ text }}
  </div>
  Old way:
  <input
    class="mt-2"
    :value="text"
    @input="(event) => (text = event.target.value)"
  />
  <br />
  Vue way: <input class="mt-2" v-model="text" />
</template>

```
### Output

<div class="bg-white p-2 text-black">
  <VModel />
</div>