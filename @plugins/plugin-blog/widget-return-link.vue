<template>
  <div class="return-link">
    <factor-link class="back" :path="setting('blog.indexRoute')">
      &larr;
      <span>{{ returnLinkText() }}</span>
    </factor-link>
  </div>
</template>
<script lang="ts">
import { factorLink } from "@factor/ui"
import { setting, stored } from "@factor/api"

export default {
  components: { factorLink },
  props: {
    postId: { type: String, default: "" },
  },
  computed: {
    post(this: any) {
      return stored(this.postId) || {}
    },
  },
  methods: {
    setting,
    returnLinkText(this: any) {
      return setting("blog.returnLinkText") || "All Posts"
    },
  },
}
</script>
<style lang="less" scoped>
.return-link {
  margin-bottom: 1rem;
}
</style>
