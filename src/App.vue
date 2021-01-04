<template>
<v-app>
    <v-navigation-drawer
      v-model="drawer"
      absolute
      bottom
      temporary
    >
     <v-list
        dense
        nav
      >
        <v-list-item
          v-for="link in links"
          :key="link.title"
          :to="link.url"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ link.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ link.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
       <v-app-bar app dark >
        <v-app-bar-nav-icon class="hidden-md-and-up" @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Ad aplication</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
              <v-btn flat v-for="link in links" :key="link.title" :to='link.url'>
 <v-icon
      medium  
      color="orange darken-2" left
    >
      {{link.icon}}
    </v-icon>
                 {{link.title}}     </v-btn>


      </v-toolbar-items> 

  </v-app-bar> 
  <v-content>
    <router-view></router-view>
  </v-content>

    </v-app>
</template>


<script>
  export default {
    data: () => ({
      drawer: false,
      group: null,
      links: [
        {
          title:'Login', icon:' mdi-lock-outline', url:'/login'
        },
                {
          title:'registration', icon:' mdi-face-outline', url:'/registration'
        },

                {
          title:'Orders', icon:' mdi-message-bookmark-outline', url:'/orders'
        },

                {
          title:'New ad', icon:' mdi-note-plus', url:'/new'
        },

                {
          title:'My ads', icon:' mdi-view-list-outline', url:'/list'
        },





      ]
    }),

    watch: {
      group () {
        this.drawer = false
      },
    },
  }
</script>