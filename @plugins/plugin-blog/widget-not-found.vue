<template>
  <div class="posts-not-found">
    <div class="text">
      <div class="title">{{ title }}</div>
      <div class="sub-title">{{ description }}</div>
    </div>
  </div>
</template>
<script lang="ts">
import { setting } from "@factor/api"

export default {
  data() {
    return {
      title: setting("blog.notFound.title"),
      description: setting("blog.notFound.subTitle"),
    }
  },
  metaInfo() {
    return {
      title: this.title,
      description: this.description,
      meta: [{ name: "robots", content: "noindex" }],
    }
  },
  created() {
    if (process) {
      process.env.factorServerStatus = "404"
    }
  },
  methods: { setting },
}
</script>
<style lang="less" scoped>
.posts-not-found {
  min-height: 50vh;
  display: flex;
  text-align: center;
  align-items: center;
  justify-content: center;
  .title {
    font-size: 1.6em;
    font-weight: var(--font-weight-bold, 700);
  }
  .sub-title {
    font-size: 1.3em;
    opacity: 0.7;
    margin-top: 1rem;
  }
}
</style>
