<template>
  <v-content>
    <v-container class="grey darken-3" :style="{'min-height': '100%'}">
      <div>
        <nuxt />
      </div>
    </v-container>
    <Footer />
  </v-content>
</template>

<script>
import Footer from '@/layouts/view/footer'

export default {
  name: 'Content',
  components: {
    Footer
  }
}
</script>
