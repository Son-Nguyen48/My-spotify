<template>
  <div
    class="sticky top-0 w-full py-4 px-6 flex items-center justify-between h-16 bg-darkest z-10"
  >
    <!-- The two navigation button: left and right  -->

    <div class="flex items-center">
      <base-button
        class="rounded-full bg-black w-8 h-8 flex items-center justify-center"
      >
        <svg
          role="img"
          height="24"
          width="24"
          aria-hidden="true"
          class="Svg-sc-ytk21e-0 kcBZLg IYDlXmBmmUKHveMzIPCF"
          viewBox="0 0 24 24"
          data-encore-id="icon"
          style="filter: brightness(0) invert(1)"
        >
          <path
            d="M15.957 2.793a1 1 0 010 1.414L8.164 12l7.793 7.793a1 1 0 11-1.414 1.414L5.336 12l9.207-9.207a1 1 0 011.414 0z"
          ></path>
        </svg>
      </base-button>
      <base-button
        class="rounded-full bg-black w-8 h-8 flex items-center justify-center ml-5"
      >
        <svg
          role="img"
          height="24"
          width="24"
          aria-hidden="true"
          class="Svg-sc-ytk21e-0 kcBZLg IYDlXmBmmUKHveMzIPCF"
          viewBox="0 0 24 24"
          style="filter: brightness(0) invert(1)"
          data-encore-id="icon"
        >
          <path
            d="M8.043 2.793a1 1 0 000 1.414L15.836 12l-7.793 7.793a1 1 0 101.414 1.414L18.664 12 9.457 2.793a1 1 0 00-1.414 0z"
          ></path>
        </svg>
      </base-button>
    </div>

    <!-- Search bar or menu favorite page -->

    <slot></slot>

    <!-- The Upgrade and User button  -->

    <div class="flex">
      <base-button
        class="text-white mr-8 font-semibold rounded-3xl h-8 pb-1 px-4 bg-light hover:bg-black hover:scale-105"
        style="border: 1px solid gray"
      >
        Upgrade
      </base-button>
      <div
        @focusout="handleFocusOut"
        @mouseover="isTitleShown = true"
        @mouseleave="isTitleShown = false"
      >
        <base-button
          @show-drop-down="showDropDown"
          class="text-white font-semibold rounded-3xl py-1 px-1 bg-black flex items-center justify-between hover:bg-light relative"
        >
          <span
            class="w-7 h-7 bg-lightest flex items-center justify-center rounded-full mr-3"
            ><svg
              role="img"
              height="16"
              width="16"
              aria-hidden="true"
              viewBox="0 0 16 16"
              data-encore-id="icon"
              class="Svg-sc-ytk21e-0 uPxdw"
              style="filter: brightness(0) invert(1)"
            >
              <path
                d="M6.233.371a4.388 4.388 0 015.002 1.052c.421.459.713.992.904 1.554.143.421.263 1.173.22 1.894-.078 1.322-.638 2.408-1.399 3.316l-.127.152a.75.75 0 00.201 1.13l2.209 1.275a4.75 4.75 0 012.375 4.114V16H.382v-1.143a4.75 4.75 0 012.375-4.113l2.209-1.275a.75.75 0 00.201-1.13l-.126-.152c-.761-.908-1.322-1.994-1.4-3.316-.043-.721.077-1.473.22-1.894a4.346 4.346 0 01.904-1.554c.411-.448.91-.807 1.468-1.052zM8 1.5a2.888 2.888 0 00-2.13.937 2.85 2.85 0 00-.588 1.022c-.077.226-.175.783-.143 1.323.054.921.44 1.712 1.051 2.442l.002.001.127.153a2.25 2.25 0 01-.603 3.39l-2.209 1.275A3.25 3.25 0 001.902 14.5h12.196a3.25 3.25 0 00-1.605-2.457l-2.209-1.275a2.25 2.25 0 01-.603-3.39l.127-.153.002-.001c.612-.73.997-1.52 1.052-2.442.032-.54-.067-1.097-.144-1.323a2.85 2.85 0 00-.588-1.022A2.888 2.888 0 008 1.5z"
              ></path></svg
          ></span>
          Nguyễn Thành ...
          <p
            class="absolute w-full text-white p-2 bg-light rounded -bottom-12 text-sm -translate-x-1/2"
            v-show="isTitleShown"
          >
            Nguyễn Thành Doanh
          </p>
          <span
            class="w-6 h-6 flex items-center justify-center rounded-full ml-3"
            ><svg
              v-if="!isShowDropDown"
              role="img"
              height="16"
              width="16"
              aria-hidden="true"
              class="Svg-sc-ytk21e-0 uPxdw eAXFT6yvz37fvS1lmt6k"
              viewBox="0 0 16 16"
              data-encore-id="icon"
              style="filter: brightness(0) invert(1)"
            >
              <path d="M14 6l-6 6-6-6h12z"></path>
            </svg>
            <svg
              v-if="isShowDropDown"
              role="img"
              height="16"
              width="16"
              aria-hidden="true"
              class="Svg-sc-ytk21e-0 uPxdw eAXFT6yvz37fvS1lmt6k"
              viewBox="0 0 16 16"
              style="filter: brightness(0) invert(1)"
              data-encore-id="icon"
            >
              <path d="M14 10L8 4l-6 6h12z"></path></svg
          ></span>
        </base-button>
        <div
          v-if="isShowDropDown === true"
          class="absolute bg-dark rounded mt-2 w-56"
          style="box-shadow: 0 1rem 2rem 2rem rgba(0, 0, 0, 0.6)"
        >
          <ul>
            <li class="mx-1">
              <base-button
                class="w-full flex items-center justify-between text-white hover:bg-light rounded px-4 py-3 text-sm"
              >
                Account
                <span
                  ><svg
                    role="img"
                    height="16"
                    width="16"
                    aria-hidden="true"
                    aria-label="External link"
                    viewBox="0 0 16 16"
                    data-encore-id="icon"
                    class="Svg-sc-ytk21e-0 uPxdw"
                    style="filter: brightness(0) invert(1)"
                  >
                    <path
                      d="M1 2.75A.75.75 0 011.75 2H7v1.5H2.5v11h10.219V9h1.5v6.25a.75.75 0 01-.75.75H1.75a.75.75 0 01-.75-.75V2.75z"
                    ></path>
                    <path
                      d="M15 1v4.993a.75.75 0 11-1.5 0V3.56L8.78 8.28a.75.75 0 01-1.06-1.06l4.72-4.72h-2.433a.75.75 0 010-1.5H15z"
                    ></path></svg
                ></span>
              </base-button>
            </li>
            <li class="mx-1">
              <base-button
                class="w-full flex items-center justify-start text-white hover:bg-light rounded px-4 py-3 text-sm"
              >
                Profile
              </base-button>
              <base-button
                class="w-full flex items-center justify-between text-white hover:bg-light rounded px-4 py-3 text-sm"
              >
                Upgrade to Premium
                <span
                  ><svg
                    role="img"
                    height="16"
                    width="16"
                    aria-hidden="true"
                    aria-label="External link"
                    viewBox="0 0 16 16"
                    data-encore-id="icon"
                    class="Svg-sc-ytk21e-0 uPxdw"
                    style="filter: brightness(0) invert(1)"
                  >
                    <path
                      d="M1 2.75A.75.75 0 011.75 2H7v1.5H2.5v11h10.219V9h1.5v6.25a.75.75 0 01-.75.75H1.75a.75.75 0 01-.75-.75V2.75z"
                    ></path>
                    <path
                      d="M15 1v4.993a.75.75 0 11-1.5 0V3.56L8.78 8.28a.75.75 0 01-1.06-1.06l4.72-4.72h-2.433a.75.75 0 010-1.5H15z"
                    ></path></svg
                ></span>
              </base-button>
            </li>
            <li class="mx-1">
              <base-button
                class="w-full flex items-center justify-between text-white hover:bg-light rounded px-4 py-3 text-sm"
              >
                Settings
              </base-button>
            </li>
            <li class="mx-1 h-px w-full bg-light"></li>
            <li class="mx-1">
              <base-button
                class="w-full flex items-center justify-between text-white hover:bg-light rounded px-4 py-3 text-sm"
              >
                Log out
              </base-button>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BaseButton from "../UI/BaseButton.vue";
export default {
  components: { BaseButton },
  data() {
    return { isTitleShown: false, isShowDropDown: false };
  },
  props: [""],
  mounted() {
    console.log(this.isTitleShown);
  },
  methods: {
    showDropDown() {
      this.isShowDropDown = !this.isShowDropDown;
    },
    handleFocusOut() {
      // do something here
      this.isShowDropDown = false;
    }
  },
  created() {
    document.addEventListener("click", this.close);
  },
  beforeDestroy() {
    document.removeEventListener("click", this.close);
  }
};
</script>

<style></style>
