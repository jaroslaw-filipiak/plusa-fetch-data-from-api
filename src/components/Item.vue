<template>
  <a :href="`${item?.url}`" class="item group">
    <div class="item__labels">
      <div class="label" v-if="item?.isAttractive">Okazja!</div>
    </div>
    <div
      class="item__photo"
      :style="`background-image: url(${item?.widePhotoUrl})`"
    >
      <div
        class="uppercase font-bold text-xl relative z-10 top-0 group-hover:-top-2 transition-all"
      >
        {{ item?.arrival?.countryName }}
      </div>
      <div
        class="text-lg relative z-10 top-0 group-hover:-top-2 transition-all"
      >
        {{ item?.arrival?.cityTo }}
      </div>
      <div
        class="text-xl bg-[#ffd200] pt-1 pb-1 pl-3 pr-3 mt-2 text-black rounded-lg font-medium relative z-10 top-0 group-hover:-top-2 transition-all"
      >
        {{ item?.price?.amount }}
        <span class="inline-flex text-[12px] relative -top-[2px]">/</span>
        {{ item?.price?.currency }}
      </div>
    </div>
    <div class="item__footer">
      <p class="item__departure">
        Odlot z: {{ item?.departure?.cityName }},
        {{ item?.departure?.airportName }}
      </p>
      <p class="item__arrival">
        Miejsce docelowe: {{ item?.arrival?.cityName }},
        {{ item?.arrival?.countryName }}
      </p>
    </div>
  </a>
</template>

<script setup>
  import { defineProps } from 'vue';

  const props = defineProps({
    item: {
      type: Object,
      required: true,
    },
  });
</script>

<style lang="scss" scoped>
  .item {
    border-radius: 4px;
    @apply min-h-[200px] bg-cover w-full relative text-black;

    &__labels {
      @apply absolute top-4 left-4 z-10;
      .label {
        @apply bg-[#ffd200] text-black pt-1 pb-1 pl-2 pr-2 rounded-md text-[12px] uppercase;
      }
    }

    &__photo {
      @apply text-white relative p-7 aspect-video rounded-xl bg-cover bg-center bg-no-repeat flex items-start flex-col justify-end;
      &:after {
        content: '';
        @apply absolute inset-0 bg-black bg-opacity-30 group-hover:bg-opacity-10 transition-all rounded-xl;
      }
    }
    &__footer {
      @apply p-4 text-black group-hover:text-black;
    }

    &__departure {
      @apply text-lg;
    }
  }
</style>
