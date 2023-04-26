<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
});
</script>

<template>
  <div>
    <h1 class="greetings">{{ msg }}</h1>
  </div>
</template>

<style scoped>
.greetings {
  text-align: center;
  font-weight: 500;
  font-size: 2.6rem;
  margin: 1rem;
  color: #2c3e50;
}

</style>
