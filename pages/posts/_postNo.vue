<template>
  <div id="post">
    <div id="titleHeader">
      Created by <span class="whiteColor">Xavy</span> on <span class="whiteColor">{{ dateToSimpleString(post.registerYmdt) }}</span><br>
      Related to <span class="whiteColor">{{ post.category.name }}</span>
    </div>

    <div id="title">
      {{ post.title }}
    </div>
    <div id="description">
      {{ post.description }}
    </div>
    <div id="body">
      <TuiViewer
        :value="post.body"
      />
    </div>
    <div id="tags">
      <span v-for="tag in post.tags" :key="tag.tagNo" class="tag">
        {{ tag.name.trim() }}
      </span>
    </div>
  </div>
</template>

<script>

import { dateToSimpleString } from '@/utils/dateUtils'

export default {
  layout: 'main',

  async asyncData({ $axios, params }) {
    const post = await $axios.$get(`/posts/${params.postNo}`)
    return { post }
  },

  methods: {
    dateToSimpleString(date) {
      return dateToSimpleString(date)
    }
  },
  head() {
    const post = this.post

    return {
      title: `${post.title}`,
      meta: [{
        hid: `iOSUrl`,
        property: 'al:ios:url'
      },
      {
        hid: `description`,
        name: 'description'
      }]
    }
  }
}
</script>

<style>
  #titleHeader {
    margin-top: 30px;
    color: gray;
  }

  .tag {
    background-color: gray;
    padding: 5px 10px;
    font-size: 18px;
    margin-right: 10px;
    border-radius: 2px;
  }

  .whiteColor {
    color: white
  }

  #title {
    font-size: 60px;
    font-weight: 800;
  }

  #description {
    font-size: 20px;
    margin-bottom: 100px;
    color: lightgray;
  }

  .tui-editor-contents pre {
    margin: 20px 0;
    font-size: 20px;
    background-color: #1f1f1f;
    padding: 20px;
    border-radius: 5px;
    color: lightgray;
  }

  pre > code {
    width: 100%;
    box-shadow: none;
    font-family: 'Nanum Gothic Coding', serif !important;
  }

  p {
    color: lightgray !important;
    font-size: 21px;
    line-height: 1.58;
    letter-spacing: -.003em;
  }

  img {
    border-radius: 3px;
    border: 1px solid gray;
  }

  h1:before {
    content: '# ';
    color: #ff734c
  }

  h2:before {
    content: '## ';
    color: #ff734c
  }

  h3:before {
    content: '### ';
    color: #ff734c
  }

  h1 {
    color: white !important;
    font-size: 40px !important;
    border-bottom: 0px solid gray !important;
  }

  h2 {
    color: white !important;
    font-size: 35px !important;
    border-bottom: 0px solid gray !important;
  }

  h3 {
    color: white !important;
    font-size: 27px !important;
  }

  blockquote {
    border-left: 4px solid #ff734c !important
  }

  blockquote > p {
    color: white !important;
  }

  strong {
    color: white;
  }

  code {
    color: white !important;
    padding: 1px 1px !important;
    border-radius: 3px !important;
    font-weight: 400;
    background: #5f5e5e;
    box-shadow: none;
    margin: 0px 5px;
  }

  a {
    color: #ff5622 !important;
  }

  ol, ul {
    color: white !important;
    font-size: 20px;
  }
</style>
