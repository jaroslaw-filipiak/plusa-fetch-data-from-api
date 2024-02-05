<template>
  <a target="_blank" :href="`${item?.url}`" class="item group">
    <div class="item__labels">
      <div class="label" v-if="item?.isAttractive">Okazja!</div>
    </div>
    <div
      class="item__photo"
      :style="`background-image: url(${item?.widePhotoUrl})`"
    >
      <div class="item__country-name">
        {{ item?.arrival?.countryName }}
      </div>
      <div class="item__arrival">
        {{ item?.arrival?.cityTo }}
      </div>
      <div class="item__price">
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
      <p class="item__destination">
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
    font-family: var(--theme-font-family);
    background-size: cover;
    position: relative;
    width: 100%;

    &:hover {
      .item__photo {
        background-size: 128%;
        transition: var(--theme-transition);
      }
      .item__arrival,
      .item__country-name,
      .item__currency {
        top: -6px;
      }
      .item__price {
      }
    }

    p {
      margin: 0;
      padding: 0;
      position: relative;
      z-index: 10;
    }

    &__labels {
      position: absolute;
      top: 1rem;
      left: 1rem;
      z-index: 10;
      .label {
        background: var(--theme-button-background-initial-color);
        color: #000;
        padding-top: 0.25rem;
        padding-bottom: 0.25rem;
        padding-left: 0.5rem;
        padding-right: 0.5rem;
        border-radius: 0.375rem;
        text-transform: uppercase;
        font-size: 12px;
      }
    }

    &__photo {
      color: var(--theme-palette-color-7);
      position: relative;
      padding: 1.75rem;
      aspect-ratio: 16 / 9;
      border-radius: 0.75rem;
      background-size: 120%;
      background-position: center;
      background-repeat: no-repeat;
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      justify-content: flex-end;
      transition: var(--theme-transition);

      @media (width <= 768px) {
        background-size: cover;
      }

      &:after {
        content: '';
        position: absolute;
        inset: 0px;
        transition: var(--theme-transition);
        border-radius: 0.75rem;
        background-color: rgba(0, 0, 0, 0.3);
      }
    }

    &__country-name {
      font-size: 24px;
      font-weight: 700;
      position: relative;
      z-index: 40;
      top: 0;
      transition: var(--theme-transition);
      color: #fff;
    }

    &__arrival {
      font-size: 1.125rem;
      transition: var(--theme-transition);
      position: relative;
      z-index: 40;
      top: 0;
      color: #fff;
    }

    &__price {
      font-size: 1.125rem;
      line-height: 1.75rem;
      padding-top: 0.25rem;
      padding-bottom: 0.25rem;
      padding-left: 0.75rem;
      padding-right: 0.75rem;
      border-radius: 0.5rem;
      font-weight: 500;
      background-color: var(--theme-palette-color-1);
      color: #000;
      transition: var(--theme-transition);
      position: relative;
      z-index: 40;
    }
    &__footer {
      padding: 1rem;
      color: var(--theme-palette-color-3);
    }

    &__departure,
    &__destination {
      font-size: 1.25rem /* 20px */;
      line-height: 1.75rem /* 28px */;
    }

    // &__destination {
    //   font-size: 1.125rem;
    //   line-height: 1.75rem;
    // }
  }
</style>
