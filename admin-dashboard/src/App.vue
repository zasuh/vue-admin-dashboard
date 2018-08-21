<template>
  <v-app>
    <v-navigation-drawer
      persistent
      :mini-variant="miniVariant"
      :clipped="clipped"
      v-model="drawer"
      enable-resize-watcher
      fixed
      app
    >
      <v-list>
        <v-list-tile>
          <v-list-tile-action>
            <img src="./assets/vue-logo.jpg" alt="" width="30px" height="30px">
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-title>VUE DASHBOARD</v-list-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-divider></v-divider>
        <v-list-group value="true">
          <v-list-tile slot="activator">
            <v-list-tile-action>
              <img src="./assets/guy.jpg" alt="" width="20px" height="20px">
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>John Smith</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>

          <v-list-tile>
            <v-list-tile-action>
              MP
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>My Profile</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>

          <v-list-tile>
            <v-list-tile-action>
              EP
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>Edit Profile</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>

          <v-list-tile>
            <v-list-tile-action>
              S
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>Settings</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list-group>
        <v-divider></v-divider>
        <v-list-tile
          value="true"
          v-for="(item, i) in items"
          :key="i"
          >
          <v-list-tile-action>
            <v-icon v-html="item.icon"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      app
      :clipped-left="clipped"
    >
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon v-html="miniVariant ? 'chevron_right' : 'chevron_left'"></v-icon>
      </v-btn>
      <v-btn icon @click.stop="clipped = !clipped">
        <v-icon>web</v-icon>
      </v-btn>
      <v-btn icon @click.stop="fixed = !fixed">
        <v-icon>remove</v-icon>
      </v-btn>
      <v-toolbar-title v-text="title"></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon @click.stop="rightDrawer = !rightDrawer">
        <v-icon>menu</v-icon>
      </v-btn>
    </v-toolbar>
    <v-content>
      <Dashboard/>
    </v-content>
    <v-navigation-drawer
      temporary
      :right="right"
      v-model="rightDrawer"
      fixed
      app
    >
      <v-list>
        <v-list-tile @click="right = !right">
          <v-list-tile-action>
            <v-icon>compare_arrows</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>Switch drawer (click me)</v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-footer :fixed="fixed" app>
      <span>Žane Suhadolnik &copy; 2017</span>
    </v-footer>
  </v-app>
</template>

<script>
import Dashboard from './components/Dashboard'

export default {
  name: 'App',
  components: {
    Dashboard
  },
  data () {
    return {
      clipped: false,
      drawer: true,
      fixed: false,
      items: [{
        icon: 'home',
        title: 'Dashboard'
      },
      {
        icon: 'pages',
        title: 'Pages'
      },
      {
        icon: 'grid_on',
        title: 'Components'
      },
      {
        icon: 'assignment',
        title: 'Forms'
      },
      {
        icon: 'view_agenda',
        title: 'Tables'
      },
      {
        icon: 'navigation',
        title: 'Maps'
      },
      {
        icon: 'widgets',
        title: 'Widgets'
      },
      {
        icon: 'bar_chart',
        title: 'Charts'
      },
      {
        icon: 'calendar_today',
        title: 'Calendar'
      }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Admin Dashboard'
    }
  }
}
</script>

<style>

</style>

