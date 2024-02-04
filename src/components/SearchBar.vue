<template>
  <div class="search-bar">
    <!-- miejsce wylotu -->
    <div class="flex items-center pt-7 pb-7 pr-7 search-bar__item">
      <label class="flex items-center gap-3" for="departure">
        <div>
          <svg width="20" height="20" viewBox="0,0,576,512">
            <path
              d="M480 192H365.71L260.61 8.06A16.014 16.014 0 0 0 246.71 0h-65.5c-10.63 0-18.3 10.17-15.38 20.39L214.86 192H112l-43.2-57.6c-3.02-4.03-7.77-6.4-12.8-6.4H16.01C5.6 128-2.04 137.78.49 147.88L32 256 .49 364.12C-2.04 374.22 5.6 384 16.01 384H56c5.04 0 9.78-2.37 12.8-6.4L112 320h102.86l-49.03 171.6c-2.92 10.22 4.75 20.4 15.38 20.4h65.5c5.74 0 11.04-3.08 13.89-8.06L365.71 320H480c35.35 0 96-28.65 96-64s-60.65-64-96-64z"
            ></path>
          </svg>
        </div>
        <p>Miejsce wylotu</p>
      </label>
      <input
        name="departure"
        type="text"
        value=""
        placeholder="Miejsce wylotu"
      />
    </div>

    <!-- miejsce przylotu -->
    <div class="flex items-center pt-7 pb-7 pr-7 search-bar__item">
      <label class="flex items-center gap-3" for="departure">
        <div>
          <svg width="20" height="20" viewBox="0,0,640,512">
            <path
              d="M115.38 136.9l102.11 37.18c35.19-81.54 86.21-144.29 139-173.7-95.88-4.89-188.78 36.96-248.53 111.8-6.69 8.4-2.66 21.05 7.42 24.72zm132.25 48.16l238.48 86.83c35.76-121.38 18.7-231.66-42.63-253.98-7.4-2.7-15.13-4-23.09-4-58.02.01-128.27 69.17-172.76 171.15zM521.48 60.5c6.22 16.3 10.83 34.6 13.2 55.19 5.74 49.89-1.42 108.23-18.95 166.98l102.62 37.36c10.09 3.67 21.31-3.43 21.57-14.17 2.32-95.69-41.91-187.44-118.44-245.36zM560 447.98H321.06L386 269.5l-60.14-21.9-72.9 200.37H16c-8.84 0-16 7.16-16 16.01v32.01C0 504.83 7.16 512 16 512h544c8.84 0 16-7.17 16-16.01v-32.01c0-8.84-7.16-16-16-16z"
            ></path>
          </svg>
        </div>
        <p>Miejsce przylotu</p>
      </label>
      <input
        name="arrival"
        type="text"
        value=""
        placeholder="Miejsce przylotu"
      />
    </div>

    <button
      @click.prevent="onClick"
      class="flex items-center gap-3 group pt-7 pb-7"
    >
      <div>
        <svg
          width="20"
          height="20"
          viewBox="0,0,448,512"
          class="rotate-90 relative left-0 group-hover:left-1 transition-all"
        >
          <path
            d="M34.9 289.5l-22.2-22.2c-9.4-9.4-9.4-24.6 0-33.9L207 39c9.4-9.4 24.6-9.4 33.9 0l194.3 194.3c9.4 9.4 9.4 24.6 0 33.9L413 289.4c-9.5 9.5-25 9.3-34.3-.4L264 168.6V456c0 13.3-10.7 24-24 24h-32c-13.3 0-24-10.7-24-24V168.6L69.2 289.1c-9.3 9.8-24.8 10-34.3.4z"
          ></path>
        </svg>
      </div>
      <div class="group-hover:underline">Filtruj</div>
    </button>
  </div>
</template>

<script setup>
  import { defineEmits } from 'vue';
  const emit = defineEmits(['handleSearch']);
  const onClick = () => {
    emit('handleSearch');
  };
</script>

<style lang="scss" scoped>
  .search-bar {
    @apply bg-[#ffd200] rounded-xl  pl-10 pr-10 text-black flex items-center justify-center gap-[30px] font-poppins;
    label {
      @apply text-[14px] mr-5;
    }

    input {
      @apply bg-white pt-3 pb-3 pl-3 pr-3 rounded border-none max-w-[220px] text-sm;
      &:focus {
        outline: none;
      }
    }

    &__item {
      @apply relative;
      &:after {
        content: '';
        @apply block w-[1px] h-[50px]  bg-[#ffa500] absolute right-0;
      }
    }
  }
</style>
