<script setup>
  // import HelloWorld from './components/HelloWorld.vue';
  import Item from './components/Item.vue';
  import SearchBar from './components/SearchBar.vue';

  import { ref, onMounted, computed } from 'vue';

  const loading = ref(false);
  const items = ref([]);

  const filteredItems = computed(() => {
    return items.value.filter(
      (item) => item?.departure?.cityName === 'Katowice'
    );
  });

  const handleSearch = () => {
    console.log('search');
  };

  const fetchData = async () => {
    loading.value = true;
    try {
      const response = await fetch(
        'https://www2.esky.pl/api/v1.0/deals.json?partner_id=PLUSA'
      );
      const data = await response.json();
      items.value = data?.deals;
      loading.value = false;
    } catch (e) {
      console.log(e);
      loading.value = false;
    }
  };

  onMounted(() => {
    fetchData();
  });
</script>

<template>
  <div class="container mt-4 mb-4 hidden">
    <SearchBar @handleSearch="handleSearch" />
  </div>

  <div
    class="container grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-[30px] items-start"
    v-if="!loading"
  >
    <Item v-for="item in filteredItems" :item="item" />
  </div>
  <div v-else>
    <div class="container text-center pt-3 pb-3">
      <p class="text-2xl">Wczytuje dane...</p>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
