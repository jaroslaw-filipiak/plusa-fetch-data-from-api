<script setup>
  // import HelloWorld from './components/HelloWorld.vue';
  import Item from './components/Item.vue';
  // import SearchBar from './components/SearchBar.vue';

  import { ref, onMounted, computed } from 'vue';

  const loading = ref(false);
  const items = ref([]);
  const error = ref(false);

  const filteredItems = computed(() => {
    // return items.value.filter(
    //   (item) => item?.departure?.cityName === 'Katowice'
    // );
    return items.value;
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
      console.log(e);
      loading.value = false;
      error.value = true;
    }
  };

  onMounted(() => {
    fetchData();
  });
</script>

<template>
  <!-- <div class="container mt-4 mb-4 hidden">
    <SearchBar @handleSearch="handleSearch" />
  </div> -->

  <div class="items-wrapper" v-if="!loading">
    <Item v-for="item in filteredItems" :item="item" />
  </div>
  <div v-else>
    <div class="items-wrapper__loading">
      <p class="text-2xl">Wczytuje dane...</p>
    </div>
  </div>
  <div class="items-wrapper__error" v-if="error">
    <p class="text-2xl">
      Wystąpił bład, nie udało się pobrać danych. Spróbuj ponownie później.
    </p>
  </div>
</template>

<style lang="scss" scoped>
  .items-wrapper {
    display: grid;
    align-items: grid-start;
    justify-items: grid-start;
    grid-template-columns: repeat(1, minmax(0, 1fr));
    gap: 30px;
    @media (min-width: 768px) {
      grid-template-columns: repeat(2, minmax(0, 1fr));
    }
    @media (min-width: 1024px) {
      grid-template-columns: repeat(3, minmax(0, 1fr));
    }

    &__error,
    &__loading {
      font-size: 1.5rem;
      line-height: 2rem;
      padding-top: 0.75rem;
      padding-bottom: 0.75rem;
      text-align: center;
    }
  }

  .items-wrapper > :nth-last-child(-n + 2) {
    display: none;
  }
</style>
