<template>
  <div>
    <div
      class="song w-full h-full p-4 rounded-lg bg-nearly__lightest hover:bg-light relative top-0 left-0 right-0"
    >
      <div
        class="play__button--green w-full h-full flex items-end justify-end p-8 absolute"
      >
        <div
          class="bg-green w-12 h-12 rounded-full flex items-center justify-center shadow-sm shadow-black hover:scale-105"
        >
          <svg
            role="img"
            height="24"
            width="24"
            aria-hidden="true"
            viewBox="0 0 24 24"
            data-encore-id="icon"
            class="Svg-sc-ytk21e-0 uPxdw"
          >
            <path
              d="M7.05 3.606l13.49 7.788a.7.7 0 010 1.212L7.05 20.394A.7.7 0 016 19.788V4.212a.7.7 0 011.05-.606z"
            ></path>
          </svg>
        </div>
      </div>
      <img
        :src="`${recent.src}`"
        alt="img"
        :class="`${isRoundedFull===true? 'h-40': 'h-auto'} w-full shadow mb-2 ${
          isRoundedFull ===true ? 'rounded-full' : 'rounded'
        }`"
      />
      <h1 class="text-sm font-semibold text-white tracking-wide">
        {{ recent.title }}
      </h1>
      <h2 class="text-xs text-lightest tracking-wide">
        {{ recent.artist }}
      </h2>
    </div>
  </div>
</template>

<script>
export default {
  props: ["recent", "isRoundedFull"]
};
</script>

<style></style>
