<template>
  <v-container
    class="fill-height test"
    fluid
  >
    <v-row>
      <v-col cols="12" align="center">
        <img :src="require('@/assets/ebook-logo-bg.svg')" alt="Taiwan EBook">
        <p>台灣電子書搜尋</p>
        <v-form ref="form" @submit.prevent="redirectToSearch" >
          <v-text-field
            v-model="searchword"
            append-icon="search"
            label="Solo"
            solo
            clearable
            :placeholder="searchbarPlaceholder"
            @click:append="redirectToSearch"
            @keydown.enter="redirectToSearch"
          ></v-text-field>
        </v-form>

        <FollowUsOnTwitter class="component-follow-us"></FollowUsOnTwitter>
        <v-tooltip
          bottom
          color="white"
          max-width="320"
          v-model="isTooltipShow"
        >
          <span
            slot="activator"
            class="theme-color"
            @click="isTooltipShow = !isTooltipShow">
              8 間台灣線上電子書店
          </span>
          <v-layout row wrap>
            <v-flex v-for="(company, key) in companies" :key='key' xs6 my-2>
              <v-avatar
                size="32">
                <img :src="`img/${company.value}.png`" :alt="company.name">
              </v-avatar>
              <span class="ma-2 grey--text text--darken-1">{{ company.name }}</span>
            </v-flex>
          </v-layout>
        </v-tooltip>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import FollowUsOnTwitter from '@/components/common/FollowUsOnTwitter.vue';

export default {
  name: 'Home',

  components: {
    FollowUsOnTwitter,
  },

  data: () => ({
    searchword: '',
    isTooltipShow: false,
    companies: [
      { name: 'Readmoo 讀墨', value: 'readmoo' },
      { name: '博客來', value: 'booksCompany' },
      { name: '樂天 kobo', value: 'kobo' },
      { name: 'Google Play 圖書', value: 'playStore' },
      { name: 'Pubu 電子書城', value: 'pubu' },
      { name: 'BOOKWALKER', value: 'bookWalker' },
      { name: 'Taaze 讀冊生活', value: 'taaze' },
      { name: 'HyRead 電子書', value: 'hyread' },
    ],
  }),

  computed: {
    isBreakpointSmAndDown() {
      return this.$vuetify.breakpoint.smAndDown;
    },

    searchbarPlaceholder() {
      return this.isBreakpointSmAndDown
        ? '搜尋書名或 ISBN'
        : '搜尋您想比價的電子書名關鍵字或 ISBN';
    },
  },

  methods: {
    redirectToSearch() {
      if (this.searchword === '') return;
      this.$router.push({ path: 'search', query: { q: this.searchword } });
    },
  },
};
</script>

<style lang="scss" scoped>
@import '~vuetify/src/styles/styles.sass';
@import '@/assets/scss/vars/index.scss';

// .vertical-divider {
//   border-left: 1px solid;
// }

// .theme-color {
//   color: #0eb29a;
// }

// a {
//   text-decoration: none;
// }

.component-follow-us {
  border-right: 1px solid $md-grey-400;
  padding-right: 1.5rem;
  margin-right: 1.5rem;

  @media #{map-get($display-breakpoints, 'sm-and-down')} {
    display: none;
  }
}

// .test {
//   color: red;

//   @media #{map-get($display-breakpoints, 'md-and-down')} {
//     color: blue;
//   }
// }
</style>
