<template>
  <div class="w-full" style="height: 100vh-90px">
    <section>
      <!-- The Recently played -->

      <div class="px-6 py-4">
        <!-- Header of The Recently played -->

        <base-header :name="'Recently played'"></base-header>

        <!-- The list played songs  -->

        <div class="w-full flex flex-wrap gap-6 mt-3">
          <base-card
            v-for="recent in recents"
            :recent="recent"
            :key="recent.title"
            class="w-48"
            style="max-width: 242px; min-height: 283.38px"
          ></base-card>
        </div>
      </div>

      <!-- Good Evening -->

      <div class="px-6 py-4">
        <!-- Header of The Recently played -->

        <base-header :name="'Good Evening'"></base-header>

        <!-- The list played songs  -->

        <div class="w-full flex flex-wrap gap-6 mt-3">
          <div
            v-for="recent in recents"
            :key="recent.title"
            style="width: 31.8%"
          >
            <div
              class="song rounded-lg bg-nearly__lightest hover:bg-light flex"
              style="min-width: 270px; height: 80px"
            >
              <img
                :src="`${recent.src}`"
                alt="img"
                class="w-auto h-full shadow mb-2 rounded"
                style="min-height: 80px; min-width: 80px"
              />
              <div class="flex items-center justify-between w-full px-4">
                <h1 class="text-sm font-semibold text-white tracking-wide">
                  {{ recent.title }}
                </h1>
                <div
                  class="play__button--green w-12 h-12 flex items-center justify-center"
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
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="px-6 py-4">
        <!-- Header of The Recently played -->

        <base-header :name="'Recently played'"></base-header>

        <!-- The list played songs  -->

        <div class="w-full flex flex-wrap gap-6 mt-3">
          <base-card
            v-for="recent in recents"
            :recent="recent"
            :key="recent.title"
            class="w-48"
            style="max-width: 242px; min-height: 283.38px"
          ></base-card>
        </div>
      </div>

      <div class="px-6 py-4">
        <!-- Header of The Recently played -->

        <base-header :name="'Suggested artists'"></base-header>

        <!-- The list played songs  -->

        <div class="w-full flex flex-wrap gap-6 mt-3">
          <base-card
            v-for="recent in artists"
            :recent="recent"
            :key="recent.title"
            :isRoundedFull="true"
            class="w-48"
            style="max-width: 242px; min-height: 283.38px"
          ></base-card>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import BaseHeader from "../UI/BaseHeader.vue";
import BaseCard from "../UI/BaseCard.vue";
export default {
  props: ["recents", "artists", "recommends"],
  components: {
    BaseHeader,
    BaseCard
  }
};
</script>

<style></style>
