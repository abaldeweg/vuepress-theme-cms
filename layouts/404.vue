<template>
  <b-app>
    <b-masthead>
      <b-masthead-item type="center">
        <router-link :to="{path: '/'}">
          <img
            :src="$withBase('/' + $site.themeConfig.logo)"
            :alt="$site.title"
            v-if="$site.themeConfig.logo"
          />
          <span v-else>
            {{ $site.title }}
          </span>
        </router-link>
      </b-masthead-item>
    </b-masthead>

    <b-content>
      <b-container :size="containerWidth" align="right" v-if="nav">
        <ul class="nav">
          <li class="nav_item" v-for="item in nav" :key="nav.link">
            <router-link :to="item.link">{{item.text}}</router-link>
          </li>
        </ul>
      </b-container>

      <b-container :size="containerWidth">
        <h1>Error 404</h1>
        <p>Could not find the requested page.</p>

        <router-link :to="{ path: '/' }">
          Back to homepage
        </router-link>

        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 500 250"
          class="beach"
          title="Beach"
        >
          <path
            d="M 436.56055 19.894531 L 436.56055 33.148438 A 26.589194 26.035387 0 0 0 423.58789 38.388672 L 414.03125 29.03125 L 409.33203 33.632812 L 418.90234 43.003906 A 26.589194 26.035387 0 0 0 413.5293 55.693359 L 400 55.693359 L 400 62.201172 L 413.53711 62.201172 A 26.589194 26.035387 0 0 0 418.88867 74.902344 L 409.33203 84.259766 L 414.03125 88.863281 L 423.60352 79.490234 A 26.589194 26.035387 0 0 0 436.56055 84.751953 L 436.56055 98 L 443.20703 98 L 443.20703 84.746094 A 26.589194 26.035387 0 0 0 456.17969 79.505859 L 465.73633 88.863281 L 470.43555 84.259766 L 460.86523 74.888672 A 26.589194 26.035387 0 0 0 466.23828 62.201172 L 479.76758 62.201172 L 479.76758 55.693359 L 466.23047 55.693359 A 26.589194 26.035387 0 0 0 460.87695 42.992188 L 470.43555 33.632812 L 465.73633 29.03125 L 456.16602 38.402344 A 26.589194 26.035387 0 0 0 443.20703 33.140625 L 443.20703 19.894531 L 436.56055 19.894531 z M 20 19.964844 L 20 28.642578 C 29.44791 28.643038 37.015625 36.36292 37.015625 46 L 37.017578 46 L 45.523438 46 L 45.525391 46 C 45.525838 36.36304 53.094951 28.642578 62.542969 28.642578 L 62.542969 19.964844 C 53.685446 19.964844 45.852366 24.624058 41.271484 31.65625 C 36.690821 24.62382 28.857521 19.965128 20 19.964844 z M 156.57617 54.734375 L 156.57617 64.107422 L 162.95898 64.107422 L 162.95898 54.734375 L 156.57617 54.734375 z M 160.74023 64.140625 C 165.50677 64.462335 169.81655 67.13095 173.39258 71.09375 C 177.21008 75.32414 180.41568 81.127567 183.09766 88.154297 C 188.46162 102.20779 191.67383 121.21827 191.67383 142.21289 L 239.53516 142.21289 A 79.767588 78.106165 0 0 0 160.74023 64.140625 z M 158.52344 64.167969 A 79.767588 78.106165 0 0 0 80 142.21289 L 127.86133 142.21289 C 127.86133 121.21827 131.07549 102.20776 136.43945 88.154297 C 139.12142 81.127567 142.32703 75.32415 146.14453 71.09375 C 149.65157 67.20741 153.866 64.571889 158.52344 64.167969 z M 159.76953 70.660156 C 157.03554 70.660156 154.17478 72.088801 151.1582 75.431641 C 148.14163 78.774471 145.19365 83.932396 142.70703 90.447266 C 137.73381 103.47702 134.55273 121.87995 134.55273 142.21289 L 156.57617 142.21289 L 156.57617 250 L 162.95898 250 L 162.95898 142.21289 L 184.98242 142.21289 C 184.98242 121.87995 181.80526 103.47702 176.83203 90.447266 C 174.34542 83.932396 171.39352 78.774471 168.37695 75.431641 C 165.36037 72.088801 162.50353 70.660156 159.76953 70.660156 z M 390.48242 207.72461 L 360.33984 215.63281 L 260 215.63281 L 260 220.83984 L 361.03906 220.83984 L 391.85938 212.75391 L 390.48242 207.72461 z M 271.45703 224.85156 L 264.57422 250 L 270.08008 250 L 275.53516 230.05859 L 373.73438 230.05859 L 379.18945 250 L 384.69531 250 L 377.8125 224.85156 L 271.45703 224.85156 z "
          />
        </svg>
      </b-container>

      <b-container :size="containerWidth" v-if="links">
        <ul class="nav">
          <li class="nav_item" v-for="item in links" :key="links.link">
            <router-link :to="item.link">{{item.text}}</router-link>
          </li>
        </ul>
      </b-container>
    </b-content>

    <style v-if="hasColors">
      html {
        --color-primary-10: {{ $themeConfig.colors.color10 }};
        --color-primary-05: {{ $themeConfig.colors.color05 }};
        --color-primary-00: {{ $themeConfig.colors.color00 }};
      }
    </style>
    <style v-if="$themeConfig.mastheadHeight">
      html {
        --masthead-height: {{ $themeConfig.mastheadHeight }};
      }
    </style>
  </b-app>
</template>

<script>
export default {
  name: 'not-found',
  computed: {
    nav (){
      return this.$themeConfig.nav
    },
    links (){
      return this.$themeConfig.links
    },
    hasColors() {
      if (!this.$themeConfig.colors) {
        return false
      }
      if (
        this.$themeConfig.colors.color10 &&
        this.$themeConfig.colors.color05 &&
        this.$themeConfig.colors.color00
      ) {
        return true
      }

      return false
    },
    containerWidth () {
      const width = this.$themeConfig.containerWidth
      if (!width) return 'm'
      if (['l', 'm', 's'].indexOf(width) === -1) return 'm'

      return width
    }
  }
}
</script>

<style src="@baldeweg/components/dist/components.css"/>

<style>
.header-anchor {
  display: none;
}
</style>

<style scoped>
.nav {
  list-style: none;
  padding: 0;
  margin: 0;
}
.nav_item {
  display: inline;
  margin-right: 20px;
}
.beach {
  fill: var(--color-neutral-08);
}
</style>
