<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" clipped app>
      <v-container>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title grey--text text--darken-2">
            <!-- titleをつけると大きくなる -->
            Navigation Lists
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-divider></v-divider>
      <!-- 線を引く -->

      <v-list dense nav>
        <!-- dense（密集）は空白グリッドを埋めてパッキングをするようにグリッドアイテムが自動配置される。 
        グリッドアイテムのサイズの大小をもとにパッキングの順番が決められる。 -->
        <v-list-group v-for="nav_list in nav_lists" 
        :key="nav_list.name"
        :prepend-icon="nav_list.icon"
        no-action
        :append-icon="nav_list.lists ? undefind : ''"
        >
        <template v-slot:activator>
        <v-list-item-content>
          <v-list-item-title>{{ nav_list.name }}</v-list-item-title>
        </v-list-item-content>
        </template>
          <v-list-item v-for="list in nav_list.lists" 
          :key="list.name"
          :to="list.link">
            <v-list-item-content>
              <v-list-item-title>{{list.name}}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
      </v-list>
      </v-container>
    </v-navigation-drawer>
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
      <v-btn text to="/enterprise">FOR ENTERPRISE</v-btn>
      <!-- routerのindex.jsに記述あり -->
      <v-menu offset-y>
        <template v-slot:activator="{on}">
          <!-- 特定の条件時(クリック時・ホバー時のみなど）のみポップアップする場合のトリガー用のスロットとして用意されている。 -->
        <v-btn text v-on="on">SUPPORT<v-icon>mdi-menu-down</v-icon></v-btn>
        <!-- v-iconで挟む、mdi-アイコン名（公式サイトにある） -->
        </template>
        <v-list>
          <v-subheader>Get help</v-subheader>
        <v-list-item v-for="support in supports" 
        :key="support.name"
        :to="support.link">
          <v-list-item-icon>
            <v-icon>{{support.icon}}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
          <v-list-item-title>{{ support.name }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        </v-list>
      </v-menu>
    </v-toolbar-items>
    </v-app-bar>
        <v-main>
          <router-view></router-view>
        </v-main>
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
  {
    name: 'Consulting and suppourt',
    icon: 'mdi-vuetify',
    link:'/consulting-and-support'
  },
  {
    name: 'Discord community',
    icon: 'mdi-discord',
    link:'/discord-community'},
  {
    name: 'Report a bug',
    icon: 'mdi-bug',
    link:'/report-a-bug'
  },
  {
    name: 'Github issue board',
    icon: 'mdi-github-face',
    link:'/guthub-issue-board'
  },
  {
    name: 'Stack overview',
    icon: 'mdi-stack-overflow',
    link:'/stack-overview'
  },
],
      // mdi-のつけ忘れに注意
    nav_lists:[
    {
      name: 'Getting Started',
      icon: 'mdi-speedometer',
      lists:[{name:'Quick Start',link:'/quick-start'},
      {name:'Pre-made layouts',link:'/pre-made-layouts'}]
    },
    {
      name: 'Customization',
      icon: 'mdi-cogs' 
    },
    {
      name: 'Styles & animations',
      icon: 'mdi-palette',
      lists:['Colors','Content','Display']
    },
    {
      name: 'UI Components',
      icon: 'mdi-view-dashboard',
      lists:['API explorer','Alerts']
    },
    {
      name: 'Directives',
      icon: 'mdi-function'
    },
    {
      name: 'Preminum themes',
      icon: 'mdi-vuetify'
    },
  ]
}
},
};
</script>
