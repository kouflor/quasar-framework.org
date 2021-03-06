title: CSS Transitions
---

CSS Transitions can be handled by the [Vue Transition Component](https://vuejs.org/v2/guide/transitions.html). The transitions are used for entering (appearing) or leaving (disappearing) animations.

However, Quasar can supply a big list of ready to use CSS animations. The animation effects are borrowed from [Animate.css](https://daneden.github.io/animate.css/). So there are 12 general, 32 entering (In) and 32 leaving (Out) animation types currently available for you to use out of the box. Check the list either on Animate.css website or on the demo available for this page.
<input type="hidden" data-fullpage-demo="animation/transition">

> Please refer to [Vue Documentation Website](https://vuejs.org/v2/guide/transitions.html) for learning on how to use the Vue supplied `<transition>` component.

## Installation
Edit `/quasar.conf.js`.
```js
// embedding all animations
animations: 'all'

// or embedding only specific animations
animations: [
  'bounceInLeft',
  'bounceOutRight'
]
```

If you are building a website, you can also skip configuring quasar.conf.js and use a CDN link which points to Animate.css like this (following is just an example, Google for latest link). Remember this will require an Internet connection for your user, as opposed to bundling from within quasar.conf.js.

```html
<!-- index.template.html -->
<head>
  ...

  <!-- CDN example for Animate.css -->
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.5.2/animate.min.css"
  >
</head>
```

## Basic Usage
Notice the string "animated" in front of the actual animation name.
``` html
<!-- Example with wrapping only one DOM element / component -->
<transition
  appear
  enter-active-class="animated fadeIn"
  leave-active-class="animated fadeOut"
>
  <!-- Wrapping only one DOM element, defined by QBtn -->
  <q-btn
    color="secondary"
    icon="mail"
    label="Email"
  />
</transition>
```

### Wrapping Multiple Elements
You can also group components or DOM elements in a transition so that the same effects are applied to all of them simultaneously.

``` html
<!-- Example with wrapping multiple DOM elements / components -->
<transition-group
  appear
  enter-active-class="animated fadeIn"
  leave-active-class="animated fadeOut"
>
  <!-- We wrap a "p" tag and a QBtn -->
  <p key="text">
     Lorum Ipsum
  </p>
  <q-btn
    key="email-button"
    color="secondary"
    icon="mail"
    label="Email"
  />
</transition-group>
```

Please note some things in the above example:

1. Note `<transition-group>` instead of `<transition>`.
2. The components and DOM elements must be keyed, like `key="text"` or `key="email-button"` in the example above.
3. Both examples above have the Boolean property `appear` specified, which makes the entering animation kick in right after component(s) have been rendered. This property is optional.

