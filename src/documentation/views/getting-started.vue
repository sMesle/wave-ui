<template lang="pug">
div
  h1.headline
    | Wave UI
  P An emerging new UI framework for Vue.js with only the bright side.
  p Like other UI frameworks, it is very flexible and easy to use. But Wave UI is also:
  ul
    li Lightweight
    li Very easy to override via CSS
    li No #[span.code !important] everywhere
    li No useless DOM wrappers inside UI elements
    li A single #[span.code $base-font-size] variable rules all the sizes and spacings

  h2 Presets
  h3 Buttons
  span.code w-button { small: true, outlined: true, round: true }
</template>

<script>
export default {
}
</script>