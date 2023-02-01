<template>
  <div class="w-60 bg-black h-full flex-none">
    <!-- This is a logo  -->

    <div class="p-6">
      <a href="#">
        <img
          class="h-10"
          src="../../../public/Spotify_Logo_CMYK_Black.png"
          style="filter: brightness(0) invert(1)"
          alt="logo"
        />
      </a>
    </div>

    <!-- This is 3 button menu: Home, search, and your library  -->

    <div class="mx-2 mb-5">
      <base-button
        @click="setID(index)"
        v-for="(page, index) in pages"
        :index="index"
        @set-id="setID"
        :key="page.id"
        :class="`focus:outline-none text-sm font-bold rounded w-full px-3 py-2 ${
          idButton === page.id ? 'bg-light text-white' : 'text-lightest'
        }`"
      >
        <router-link :to="page.link" class="flex items-center justify-start">
          <span
            v-html="idButton === page.id ? page.iconActive : page.icon"
            style="filter: brightness(0) invert(1)"
            class="mx-1"
          >
          </span>
          <p class="mx-3">{{ page.name }}</p>
        </router-link>
      </base-button>
    </div>

    <!-- This is 2 button Create Playlist and Liked Songs  -->

    <div class="mx-5">
      <h1
        class="text-xs font-semibold text-lightest tracking-widest uppercase mb-2"
      >
        Playlists
      </h1>
      <base-button class="opacity-75 hover:opacity-100 mb-3">
        <div
          class="w-6 h-6 bg-white rounded flex items-center justify-center mr-3"
        >
          <svg
            role="img"
            height="12"
            width="12"
            aria-hidden="true"
            viewBox="0 0 16 16"
            data-encore-id="icon"
            class="Svg-sc-ytk21e-0 uPxdw"
          >
            <path
              d="M15.25 8a.75.75 0 01-.75.75H8.75v5.75a.75.75 0 01-1.5 0V8.75H1.5a.75.75 0 010-1.5h5.75V1.5a.75.75 0 011.5 0v5.75h5.75a.75.75 0 01.75.75z"
            ></path>
          </svg>
        </div>
        <p class="text-white font-semibold">Create Playlist</p>
      </base-button>
      <base-button class="opacity-75 hover:opacity-100">
        <div
          class="w-6 h-6 rounded flex items-center justify-center mr-3"
          style="background: linear-gradient(135deg, #450af5, #c4efd9)"
        >
          <svg
            role="img"
            height="12"
            width="12"
            aria-hidden="true"
            viewBox="0 0 16 16"
            data-encore-id="icon"
            class="Svg-sc-ytk21e-0 uPxdw"
            style="filter: brightness(0) invert(1)"
          >
            <path
              d="M15.724 4.22A4.313 4.313 0 0012.192.814a4.269 4.269 0 00-3.622 1.13.837.837 0 01-1.14 0 4.272 4.272 0 00-6.21 5.855l5.916 7.05a1.128 1.128 0 001.727 0l5.916-7.05a4.228 4.228 0 00.945-3.577z"
            ></path>
          </svg>
        </div>
        <p class="text-white font-semibold">Liked Songs</p>
      </base-button>
      <div class="h-px w-full bg-light my-3"></div>
    </div>

    <!-- This is playlist detail  -->

    <div class="mx-5">
      <div class="playlist-detail w-full h-32 overflow-y-scroll">
        <base-button
          v-for="album in albums"
          :key="album.name"
          class="opacity-75 hover:opacity-100"
        >
          <p class="text-lightest hover:text-white py-1">
            {{ album.name }}
          </p>
        </base-button>
      </div>
    </div>

    <div class="mx-5 py-2">
      <base-button
        class="flex items-center justify-start opacity-75 hover:opacity-100 p-3"
      >
        <svg
          role="img"
          height="24"
          width="24"
          aria-hidden="true"
          viewBox="0 0 24 24"
          data-encore-id="icon"
          class="Svg-sc-ytk21e-0 uPxdw mr-3"
          style="filter: brightness(0) invert(1)"
        >
          <path
            d="M12 3a9 9 0 100 18 9 9 0 000-18zM1 12C1 5.925 5.925 1 12 1s11 4.925 11 11-4.925 11-11 11S1 18.075 1 12z"
          ></path>
          <path
            d="M12 6.05a1 1 0 011 1v7.486l1.793-1.793a1 1 0 111.414 1.414L12 18.364l-4.207-4.207a1 1 0 111.414-1.414L11 14.536V7.05a1 1 0 011-1z"
          ></path>
        </svg>

        <p class="text-white font-semibold">Install App</p>
      </base-button>
    </div>
  </div>
</template>

<script>
import BaseButton from "../UI/BaseButton.vue";
export default {
  components: {
    BaseButton
  },
  data() {
    return {};
  },
  props: ["pages", "albums", "idButton"],
  mounted() {
    console.log(this.pages, this.setID, this.idButton);
  },
  updated() {
    console.log(this.idButton);
  },
  methods: {
    setID(index) {
      this.$emit("set-id", index);
    }
  }
};
</script>

<style></style>
