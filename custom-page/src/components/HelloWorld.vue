<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
});
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
  </div>
</template>

<style scoped>
.greetings h1 {
  text-align: center;
  font-weight: 500;
  font-size: 2.6rem;
  margin: 1rem;
  color: #2c3e50;
}

</style>
