<template>
  <ul>
    <!-- SCOPED SLOTS -->
    <li v-for="goal in goals" :key="goal">
      <slot :item="goal" another="test"></slot>
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      goals: ['this is a string', 'number2']
    }
  }
}
</script>