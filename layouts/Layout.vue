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
        <Content/>
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
  name: 'layout',
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
</style>
