<template>
  <v-app>
    <v-app-bar color="primary" dark app>
      <!-- darkはvuetify上で用意されたテーマ。appを設定すると自動で高さを調節してくれる -->
      <!-- colorは背景色。color=色--textで文字色「-」は二個 -->
      <v-toolbar-title>Vuetify</v-toolbar-title>
    </v-app-bar>
    <v-footer dark app>Vuetify</v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  components: {
    
  },

  data: () => ({
    //
  }),
};
</script>
