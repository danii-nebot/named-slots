<script setup>
import AlertBox from './components/AlertBox.vue';
</script>

<template>
  <AlertBox type="WARNING">
    <!-- no content, will display fallbacks -->
  </AlertBox>

  <br />
  <hr />
  <br />

  <AlertBox>
    <template #header> Dismissable Error </template>
    <!-- main content -->
    Something terrible happened
    <template #footer>
      <button @click="">Accept</button>
      <button>oh no!</button>
    </template>
  </AlertBox>
</template>

<style scoped>
button {
  margin: 10px;
}
</style>
