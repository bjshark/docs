<template>
  <v-app
    id="sandbox"
    :dark="dark"
    :light="!dark"
    standalone
  >
    <v-navigation-drawer
      v-model="primaryDrawer.model"
      :permanent="primaryDrawer.type === 'permanent'"
      :persistent="primaryDrawer.type === 'persistent'"
      :temporary="primaryDrawer.type === 'temporary'"
      :clipped="primaryDrawer.clipped"
      :floating="primaryDrawer.floating"
      :mini-variant="primaryDrawer.mini"
      absolute
      overflow
      enable-resize-watcher
    ></v-navigation-drawer>
    <v-toolbar>
      <v-toolbar-side-icon @click.native.stop="primaryDrawer.model = !primaryDrawer.model" v-if="primaryDrawer.type !== 'permanent'"></v-toolbar-side-icon>
      <v-toolbar-title>Vuetify</v-toolbar-title>
    </v-toolbar>
    <main>
      <v-container fluid>
        <v-layout align-center justify-center>
          <v-flex xs10>
            <v-card>
              <v-card-text>
                <v-layout row wrap>
                  <v-flex xs12 md6>
                    <span>Scheme</span>
                    <v-switch primary label="Dark" v-model="dark"></v-switch>
                  </v-flex>
                  <v-flex xs12 md6>
                    <span>Drawer</span>
                    <v-radio
                      primary
                      :label="drawer"
                      v-model="primaryDrawer.type"
                      :value="drawer.toLowerCase()"
                      v-for="drawer in drawers"
                      :key="drawer"
                    ></v-radio>
                    <v-switch label="Clipped" v-model="primaryDrawer.clipped" primary></v-switch>
                    <v-switch label="Floating" v-model="primaryDrawer.floating" primary></v-switch>
                    <v-switch label="Mini" v-model="primaryDrawer.mini" primary></v-switch>
                  </v-flex>
                  <v-flex xs12 md6>
                    <span>Footer</span>
                    <v-switch label="Fixed" v-model="footer.fixed" primary></v-switch>
                  </v-flex>
                </v-layout>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn flat>Cancel</v-btn>
                <v-btn flat primary>Submit</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </main>
    <v-footer :absolute="footer.fixed">
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    data: () => ({
      dark: true,
      drawers: ['Permanent', 'Persistent', 'Temporary'],
      primaryDrawer: {
        model: true,
        type: 'persistent',
        clipped: false,
        floating: false,
        mini: false
      },
      footer: {
        fixed: false
      }
    })
  }
</script>

<style>
  #sandbox {
    border: 1px solid rgba(0, 0, 0, .1);
    overflow: hidden;
  }
  #sandbox .container, #sandbox {
    min-height: 700px;
  }
</style>
