<template>
  <a class="follow-us-link" href="https://twitter.com/TaiwanEBook">
    <i class="fab fa-twitter follow-us-icon grey-text text--lighten-2"></i>
    <span class="follow-us-text">在推特上追蹤我們</span>
  </a>
</template>

<script>
export default {
  name: 'FollowUsOnTwitter',
};
</script>

<style lang="scss" scoped>
@import '@/assets/scss/vars/index.scss';

.follow-us-link {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  color: $md-grey-500;

  .follow-us-icon {
    font-size: 1.5rem;
    margin-right: 0.3rem;
  }

  .follow-us-text {
    font-size: 1rem;
  }
}
</style>
