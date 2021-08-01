<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" clipped app>Navigation Lists</v-navigation-drawer>
    <!-- 画面サイズによってサイドバーが表示・非表示される。ユーザーで操作するためにハンバーガーメニューを作る -->
    <!-- clippedを設定することで、ナビゲーションバーの下に表示する。-->
    <v-app-bar color="primary" clipped-left dark app>
      <!-- darkはvuetify上で用意されたテーマ。appを設定すると自動で高さを調節してくれる -->
      <!-- colorは背景色。color=色--textで文字色「-」は二個 -->
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <!-- ハンバーガーメニュー,drawerは提議していなくてもドキュメントに記述されているため、dataで定義すれば扱える -->
      <v-toolbar-title>Vuetify</v-toolbar-title>
      <v-spacer></v-spacer>
      <!-- 次の要素との間を開ける -->
      <!-- <v-btn text>button</v-btn> -->
      <!-- textを設定すると背景と同じ色になって、結果透明に見える -->
      <!-- <v-btn outlined>button</v-btn> -->
      <!-- outlinedで枠線だけの表示 -->
    <v-toolbar-items>
      <!-- v-toolbar-itemsに入れることで、バーいっぱいに選択領域が拡大する -->
      <v-btn text>FOR ENTERPRISE</v-btn>
      <v-menu offset-y>
        <template v-slot:activator="{on}">
          <!-- 特定の条件時(クリック時・ホバー時のみなど）のみポップアップする場合のトリガー用のスロットとして用意されている。 -->
        <v-btn text v-on="on">SUPPORT</v-btn>
        </template>
        <v-list>
          <v-subheader>Get help</v-subheader>
        <v-list-item v-for="support in supports" :key="support">
          <v-list-item-content>
          <v-list-item-title>{{ support }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        </v-list>
      </v-menu>
    </v-toolbar-items>
    </v-app-bar>
        
    <v-footer dark app>Vuetify</v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{
      drawer: null,
      supports:[
          'Consulting and suppourt',
          'Discord community',
          'Report a bug',
          'Github issue board',
          'Stack overview'
        ]
    }
  },
};
</script>
