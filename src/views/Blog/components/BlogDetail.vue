<template>
  <div class="blogDetail-container">
    <h1>{{ blog.title }}</h1>
    <div class="aside">
      <span>日期: {{ formatDate(blog.createDate) }}</span>
      <span>浏览: {{ blog.scanNumber }}</span>
      <a href="#data-form-container">评论: {{ blog.commentNumber }}</a>
      <RouterLink
        :to="{
          name: 'CategoryBlog',
          params: {
            categoryId: blog.category.id,
          },
        }"
        >{{ blog.category.name }}</RouterLink
      >
    </div>
    <div v-html="blog.htmlContent" class="markdown-body"></div>
  </div>
</template>

<script>
import formatDate from "@/utils/formatDate";
import "@/styles/markdown.css";
import "highlight.js/styles/github.css";

export default {
  props: {
    blog: {
      type: Object,
      required: true,
    },
  },
  methods: {
    formatDate,
  },
};
</script>

<style lang="less" scoped>
@import "~@/styles/var.less";
.blogDetail-container {
  padding: 20px;
  width: 100%;
  h1 {
    margin: 22px 0;
  }
}
.aside {
  font-size: 13px;
  color: @gray;
  span,
  a {
    margin-right: 15px;
  }
}
.markdown-body {
  margin: 2em 0;
}
</style>
