<template>
  <div class="nav-toc-container">
    <nav class="nav-toc">
      <div class="asset-download-btn-wrapper" cds-layout="m-b:md" v-if="isOnIconsPage">
        <a
          class="btn btn-outline asset-download-btn"
          target="_blank"
          href="https://github.com/vmware/clarity-assets/archive/master.zip"
          >download svg icons</a
        >
      </div>
      <b class="title">Content</b>
      <TOC />
    </nav>
  </div>
</template>

<script>
export default {
  props: {
    sticky: { type: Boolean, default: false },
  },
  computed: {
    isOnIconsPage: function () {
      return this.$route.path === '/foundation/icons/';
    },
  },
};
</script>

<style lang="scss">
.nav-toc-container {
  width: 100%;
  padding: 0 0 var(--cds-token-space-size-9);

  .nav-toc {
    max-height: calc(100vh - 3rem);
    overflow-y: auto;

    padding-left: var(--cds-token-space-size-4);
    padding-right: var(--cds-token-space-size-4);
    max-width: inherit;
  }

  @media (min-width: 992px) {
    --nav-toc-width: 12rem;
    width: var(--nav-toc-width);
    position: absolute;
    top: 0;
    right: calc(-1 * var(--nav-toc-width));
    border-bottom: none;
    background-color: transparent;

    .nav-toc {
      position: fixed;
      top: 8.1rem;
      padding-bottom: 8.1rem;
      padding-left: var(--cds-token-space-size-9);
      padding-right: var(--cds-token-space-size-9);
    }
  }

  .title {
    padding-left: 6px;
    text-transform: uppercase;
  }

  ul {
    padding: 0;
    margin: 0;
  }
  li {
    list-style: none;
    padding-top: 0.5rem;
    a {
      padding: 0 var(--cds-token-space-size-4);
      display: inline-block;
      color: var(--cds-token-color-neutral-700, #666);
      &:hover {
        text-decoration: none;
      }
      &:visited {
        color: var(--cds-token-color-neutral-700, #666);
      }
      &.router-link-active {
        color: var(--cds-token-color-neutral-1000, #000);
      }
    }
  }

  li a.router-link-active {
    position: relative;
    &:before {
      content: '';
      position: absolute;
      top: 0;
      left: -3px;
      width: 3px;
      height: 100%;
      background-color: #0079b8;
    }
  }
  li li {
    padding-top: 0;
    a {
      margin-left: var(--cds-token-space-size-4);
    }
  }
}
</style>
