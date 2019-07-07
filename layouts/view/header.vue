<template>
  <div>
    <v-navigation-drawer
      v-model="drawer"
      fixed
      clipped
      class="grey darken-2"
      app
      dark
      width="200"
    >
      <v-list
        dense
        class="grey darken-2"
        dark
      >
        <template v-for="(item, i) in items">
          <v-layout
            v-if="item.heading"
            :key="i"
            row
            align-center
          >
            <v-flex xs6>
              <v-subheader v-if="item.heading">
                {{ item.heading }}
              </v-subheader>
            </v-flex>
            <v-flex xs6 class="text-xs-right">
              <v-btn small flat>
                edit
              </v-btn>
            </v-flex>
          </v-layout>
          <v-divider
            v-else-if="item.divider"
            :key="i"
            dark
            class="my-3"
          />
          <v-list-tile
            v-else
            :key="i"
          >
            <v-list-tile-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>
                {{ item.text }}
              </v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </template>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar color="deep-orange" app clipped-left dark>
      <v-toolbar-side-icon @click="drawer = !drawer"></v-toolbar-side-icon>
      <span class="title ml-3 mr-5">Xavy&nbsp;<span class="font-weight-light">Atelier</span></span>
      <v-text-field
        solo-inverted
        flat
        hide-details
        label="Search"
        prepend-inner-icon="search"
      ></v-text-field>
      <v-spacer></v-spacer>
    </v-toolbar>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data: () => ({
    drawer: true,
    items: [
      { icon: 'book', text: 'Posts' },
      { icon: 'collections_bookmark', text: 'Series' },
      { divider: true },
      { icon: 'subject', text: 'Category' },
      { icon: 'view_module', text: 'Tag' },
      { divider: true },
      { icon: 'contact_support', text: 'Me' }
    ]
  })
}
</script>
