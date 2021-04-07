<template>
    <div class="hero">
        <h1 class="hero-title" v-html="settings.title" />
        <h2 class="hero-subtitle" v-html="settings.subtitle" />
    </div>
</template>

<static-query>
query {
  generals: allStrapiGeneral {
    edges {
      node {
        id
        title
        subtitle
      }
    }
  }
}
</static-query>

<script>
export default {
  data() {
    return {
    }
  },
  computed: {
    settings() {
      return {
        ...this.$static.generals.edges[0].node
      };
    }
  },
}
</script>

<style>
.hero {
    text-align: center;
    width: 480px;
    max-width: 100%;
    margin: 0 auto;
    padding: 4rem 0 8rem 0;
}

.hero-title {
    font-size: 3rem;
    font-weight: 700;
    padding: 0;
    margin: 0 0 2rem 0;
}
.hero-title p,
.hero-subtitle p {
    margin: 0;
    padding: 0;
}
.hero-subtitle {
    font-size: 1.15em;
    font-weight: 400;
    line-height: 1.68;
    padding: 0;
    margin: 0;
    opacity: 0.6;
}
</style>
