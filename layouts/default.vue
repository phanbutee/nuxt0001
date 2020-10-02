<template>
  <v-app id=gg>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app id="pp"
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app id="gg">
      
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <v-btn icon @click.stop="clipped = !clipped">
        <v-icon>mdi-application</v-icon>
      </v-btn>
      <v-btn icon @click.stop="fixed = !fixed">
        <v-icon>mdi-minus</v-icon>
      </v-btn>
      <v-toolbar-title v-text="title" />
      <v-spacer />
    </v-app-bar>
    <v-main id = "">
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Anime',
          to: '/',
        },
       
       
      ],
    
    }
  },
}
</script>

<style lang="css" scoped>
#gg {
  background-image: url("https://images.unsplash.com/photo-1554189097-ffe88e998a2b?ixlib=rb-1.2.1&w=1000&q=80");
  background-size: cover;
}
#pp {
  background-image: url("https://i.pinimg.com/originals/e3/d9/68/e3d9685c3c61e52015e51deefda6a6e6.jpg");
  background-size: cover;
}
</style>