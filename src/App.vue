<template>
  <v-app>

    <AppHeader></AppHeader>

    <v-content>
      <router-view :class="routeViewBackgoundColor"></router-view>
    </v-content>

    <v-footer class="app-footer">
      <AppFooter></AppFooter>
    </v-footer>

  </v-app>

</template>

<script>
import AppHeader from '@/components/layout/AppHeader.vue';
import AppFooter from '@/components/layout/AppFooter.vue';

export default {
  name: 'ebook-search',

  components: {
    AppHeader,
    AppFooter,
  },

  computed: {
    toolBarColor() {
      return this.$route.path === '/' ? '#f5f5f5' : '#0eb29a';
    },
    fontColor() {
      return this.$route.path === '/' ? 'grey--text text--darken-1' : 'white--text';
    },
    routeViewBackgoundColor() {
      return this.$route.path === '/' ? 'bg-grey height-100' : 'height-100';
    },
    toolBarTitleClass() {
      return this.$route.path === '/' ? 'disable-all' : 'white--text';
    },
  },
};
</script>

<style lang="scss" scoped>
@import '~vuetify/src/styles/styles.sass';
@import '@/assets/scss/vars/index.scss';

.bg-grey {
  background: $md-grey-100;
}

.app-footer {
  @media #{map-get($display-breakpoints, 'md-and-up')} {
    display: none;
  }
}
</style>

<style lang="scss">
body {
  font-family: "Microsoft JhengHei", -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>
