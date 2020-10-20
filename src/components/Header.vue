<template>
  <header class="header">
    <div>{{ titleText }}</div>
  </header>
</template>

<script>
  export default {
    name: 'Header',
    props: ['title'],
    setup({ title }) {
      return { titleText: title };
    }
  }
</script>
