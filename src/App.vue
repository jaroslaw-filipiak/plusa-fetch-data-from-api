<script setup>
  // import HelloWorld from './components/HelloWorld.vue';

  import { ref, onMounted } from 'vue';

  const loading = ref(true);
  const items = ref([]);

  const fetchData = async () => {
    const response = await fetch(
      'https://www2.esky.pl/api/v1.0/deals.json?partner_id=PLUSA'
    );
    const data = await response.json();
    items.value = data?.deals;
  };

  onMounted(() => {
    fetchData();
  });
</script>

<template>
  <pre>
    <code>{{ items.length }}</code>
  </pre>
</template>

<style scoped>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.vue:hover {
    filter: drop-shadow(0 0 2em #42b883aa);
  }
</style>
