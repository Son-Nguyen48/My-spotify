<template>
  <div id="app">
    <div class="bg-dark h-screen">
      <div class="flex" style="height: calc(100vh - 90px)">
        <!-- Side nav  -->

        <side-bar
          :pages="pages"
          :albums="albums"
          :idButton="idButton"
          @set-id="setID"
        ></side-bar>

        <!-- Main content  -->

        <div
          class="main-content w-full h-full relative bg-dark overflow-y-scroll"
        >
          <!-- Header -->
          <the-header></the-header>

          <!-- The main content -->

          <!-- <main-content
            :recents="recents"
            :artists="artists"
            :recommends="recommends"
          ></main-content> -->
          <router-view />
        </div>
      </div>

      <!-- Play bar  -->
      <player-bar></player-bar>
    </div>
  </div>
</template>

<script>
import SideBar from "./components/layouts/SideBar.vue";
import TheHeader from "./components/layouts/TheHeader.vue";
// import MainContent from "./components/layouts/MainContent.vue";
import PlayerBar from "./components/layouts/PlayerBar.vue";
export default {
  name: "App",
  data() {
    return {
      pages: [
        {
          id: "home",
          name: "Home",
          icon: `<svg role="img" height="24" width="24" aria-hidden="true" class="Svg-sc-ytk21e-0 uPxdw home-icon" viewBox="0 0 24 24" data-encore-id="icon"><path d="M12.5 3.247a1 1 0 00-1 0L4 7.577V20h4.5v-6a1 1 0 011-1h5a1 1 0 011 1v6H20V7.577l-7.5-4.33zm-2-1.732a3 3 0 013 0l7.5 4.33a2 2 0 011 1.732V21a1 1 0 01-1 1h-6.5a1 1 0 01-1-1v-6h-3v6a1 1 0 01-1 1H3a1 1 0 01-1-1V7.577a2 2 0 011-1.732l7.5-4.33z"></path></svg>`,
          iconActive: `<svg role="img" height="24" width="24" aria-hidden="true" class="Svg-sc-ytk21e-0 uPxdw home-active-icon" viewBox="0 0 24 24" data-encore-id="icon"><path d="M13.5 1.515a3 3 0 00-3 0L3 5.845a2 2 0 00-1 1.732V21a1 1 0 001 1h6a1 1 0 001-1v-6h4v6a1 1 0 001 1h6a1 1 0 001-1V7.577a2 2 0 00-1-1.732l-7.5-4.33z"></path></svg>`,
          link: "/"
        },
        {
          id: "search",
          name: "Search",
          icon: `<svg role="img" height="24" width="24" aria-hidden="true" class="Svg-sc-ytk21e-0 uPxdw search-icon" viewBox="0 0 24 24" data-encore-id="icon"><path d="M10.533 1.279c-5.18 0-9.407 4.14-9.407 9.279s4.226 9.279 9.407 9.279c2.234 0 4.29-.77 5.907-2.058l4.353 4.353a1 1 0 101.414-1.414l-4.344-4.344a9.157 9.157 0 002.077-5.816c0-5.14-4.226-9.28-9.407-9.28zm-7.407 9.279c0-4.006 3.302-7.28 7.407-7.28s7.407 3.274 7.407 7.28-3.302 7.279-7.407 7.279-7.407-3.273-7.407-7.28z"></path></svg>`,
          iconActive: `<svg role="img" height="24" width="24" aria-hidden="true" class="Svg-sc-ytk21e-0 uPxdw search-active-icon" viewBox="0 0 24 24" data-encore-id="icon"><path d="M15.356 10.558c0 2.623-2.16 4.75-4.823 4.75-2.664 0-4.824-2.127-4.824-4.75s2.16-4.75 4.824-4.75c2.664 0 4.823 2.127 4.823 4.75z"></path><path d="M1.126 10.558c0-5.14 4.226-9.28 9.407-9.28 5.18 0 9.407 4.14 9.407 9.28a9.157 9.157 0 01-2.077 5.816l4.344 4.344a1 1 0 01-1.414 1.414l-4.353-4.353a9.454 9.454 0 01-5.907 2.058c-5.18 0-9.407-4.14-9.407-9.28zm9.407-7.28c-4.105 0-7.407 3.274-7.407 7.28s3.302 7.279 7.407 7.279 7.407-3.273 7.407-7.28c0-4.005-3.302-7.278-7.407-7.278z"></path></svg>`,
          link: "/search"
        },
        {
          id: "library",
          name: "Your Library",
          icon: `<svg role="img" height="24" width="24" aria-hidden="true" class="Svg-sc-ytk21e-0 uPxdw collection-icon" viewBox="0 0 24 24" data-encore-id="icon"><path d="M14.5 2.134a1 1 0 011 0l6 3.464a1 1 0 01.5.866V21a1 1 0 01-1 1h-6a1 1 0 01-1-1V3a1 1 0 01.5-.866zM16 4.732V20h4V7.041l-4-2.309zM3 22a1 1 0 01-1-1V3a1 1 0 012 0v18a1 1 0 01-1 1zm6 0a1 1 0 01-1-1V3a1 1 0 012 0v18a1 1 0 01-1 1z"></path></svg>`,
          iconActive: `<svg role="img" height="24" width="24" aria-hidden="true" class="Svg-sc-ytk21e-0 uPxdw collection-active-icon" viewBox="0 0 24 24" data-encore-id="icon"><path d="M3 22a1 1 0 01-1-1V3a1 1 0 012 0v18a1 1 0 01-1 1zM15.5 2.134A1 1 0 0014 3v18a1 1 0 001 1h6a1 1 0 001-1V6.464a1 1 0 00-.5-.866l-6-3.464zM9 2a1 1 0 00-1 1v18a1 1 0 102 0V3a1 1 0 00-1-1z"></path></svg>`,
          link: "/yourlibrary"
        }
      ],
      idButton: "home",
      albums: [
        { name: "Drive" },
        { name: "Fly" },
        { name: "Bus" },
        { name: "Fun" },
        { name: "Funny" },
        { name: "Great" }
      ],
      recents: [
        {
          src: "https://i.scdn.co/image/ab67616d00001e020f3abcbf0e79cacac2df44cc",
          title: "City Girl",
          artist: "Flux Vortex"
        },
        {
          src: "https://seeded-session-images.scdn.co/v1/img/track/0JkBihR0VtIg6Q2TEfIvKv/en",
          title: "Not Your Baby Radio",
          artist: "By Spotify"
        },
        {
          src: "https://seed-mix-image.spotifycdn.com/v6/img/artist/00FQb4jTyendYWaN8pK0wa/en/default",
          title: "Lana Del Rey Mix",
          artist: "Conan Gray, Montell Fish, Mazzy Star and more"
        },
        {
          src: "https://i.scdn.co/image/ab67616d0000b27321c8a879ce70dc6e972c16b5",
          title: "Flux Vortex",
          artist: "Artist"
        },
        {
          src: "https://i.scdn.co/image/ab67706c0000da84e7dfed37d03b77d818d63009",
          title: "Lana Del Rey Radio",
          artist: "Julency Myrtil"
        }
      ],
      artists: [
        {
          src: "https://i.scdn.co/image/ab6761610000f178b337a18007222947ec65f65f",
          title: "Justin Degryse",
          artist: "Artist"
        },
        {
          src: "https://i.scdn.co/image/ab6761610000f17887528aedec4b8d5586768014",
          title: "Jaymes Young",
          artist: "Artist"
        },
        {
          src: "https://i.scdn.co/image/ab6761610000f1781cc12c7a616161d6646cf54c",
          title: "Famy",
          artist: "Artist"
        },
        {
          src: "https://i.scdn.co/image/ab6761610000f17877cd31579fca84c5c60eb46c",
          title: "Rosa Linn",
          artist: "Artist"
        },
        {
          src: "https://i.scdn.co/image/ab6761610000f1781d851d77d3ab7d1a29808cb3",
          title: "Johnny Orlando",
          artist: "Artist"
        }
      ],
      recommends: [
        {
          src: "https://i.scdn.co/image/ab67616d00001e020f3abcbf0e79cacac2df44cc",
          title: "City Girl",
          artist: "Flux Vortex"
        },
        {
          src: "https://i.scdn.co/image/ab67616d00001e0224f9f038e436904e82bf931b",
          title: "Go To Hell",
          artist: "Mindme"
        },
        {
          src: "https://i.scdn.co/image/ab67616d00001e02a33acf6bf3082f9d95792d8f",
          title: "Change In Me",
          artist: "Facing Waves"
        },
        {
          src: "https://i.scdn.co/image/ab67616d00001e021386a660cb4ea2ee471cc310",
          title: "I've Had Enough",
          artist: "Snake City"
        },
        {
          src: "https://i.scdn.co/image/ab6761610000f1781d851d77d3ab7d1a29808cb3",
          title: "3am Thoughts",
          artist: "Rune"
        }
      ]
    };
  },
  methods: {
    setID(index) {
      this.idButton = this.pages[index].id;
    },
    close(e) {
      if (!this.$el.contains(e.target)) {
        this.isShowDropDown = false;
      }
    },
    handleFocus() {
      // do something here
      console.log("1");
    }
  },

  components: {
    SideBar,
    TheHeader,
    // MainContent,
    PlayerBar
  }
};
</script>

<style>
.main-content::-webkit-scrollbar {
  width: 0.7em;
  transition: all 0.7s ease;
}

.main-content:hover::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
}

.main-content:hover::-webkit-scrollbar-thumb {
  background-color: darkgrey;
  outline: 1px solid slategrey;
}

.playlist-detail::-webkit-scrollbar {
  transition: all 0.7s ease;
  width: 0.6em;
}

.playlist-detail:hover::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
}

.playlist-detail:hover::-webkit-scrollbar-thumb {
  background-color: darkgrey;
  outline: 1px solid slategrey;
}

.play__button--green {
  opacity: 0;
  transform: translateY(1%);
  transition: transform 0.4s ease;
}

.song:hover .play__button--green {
  transform: translateY(-1%);
  opacity: 1;
}

.progress-bar:hover .absolute,
.volume-bar:hover .absolute {
  background-color: #1db954;
}
</style>

<!-- solution for : "Click outside to close submenu"
https://stackoverflow.com/questions/36170425/detect-click-outside-element
-->
