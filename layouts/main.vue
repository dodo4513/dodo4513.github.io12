<template>
  <v-app id="atelier" class="grey darken-3" dark>
    <Header />
    <Content />
  </v-app>
</template>

<script>
import Content from '@/layouts/view/content'
import Header from '@/layouts/view/header'

export default {
  components: {
    Content,
    Header
  }
}
</script>

<style>
  body{
    font-family: 'Nanum Gothic', sans-serif;
  }
</style>
