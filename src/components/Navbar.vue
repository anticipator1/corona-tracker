<template>
    <div id="inspire">
        <v-app-bar >
           
            <v-app-bar-nav-icon class="grey--text" @click="drawer=!drawer"></v-app-bar-nav-icon>
            <v-toolbar-title class="text--uppercase grey--text ">
                <span class="font-weight-light">Corona</span>
                <span>Tracker</span>
            </v-toolbar-title>
            <v-spacer></v-spacer>
 <v-menu offset-y>
      <template v-slot:activator="{ on }">
        <v-btn
          color="grey"
          text
          v-on="on"
        >
        <v-icon left>mdi-chevron-down</v-icon>
          <span>Menu</span>
        </v-btn>
      </template>
      <v-list>
        <v-list-item
          v-for="link in links" :key="link.text" router :to="link.route">
          <v-list-item-title>{{ link.text }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>

          
        </v-app-bar>
        <v-navigation-drawer app v-model="drawer"  class="info">
            <v-row class="text-center">
                <v-col class="mt-5">
                    <v-avatar size="100">
                        <img src="/corona.jpg" alt="">
                    </v-avatar>
                    <p class="white--text subheading mt-1">
                         Corona Tracker
                        </p>
                </v-col>
               
            </v-row>
            <v-list>
            <v-list-item v-for="link in links" :key="link.text" router :to="link.route">
                <v-list-item-action>
                    <v-icon class="white--text">
                      {{link.icon}} 
                    </v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title>
                        {{link.text}}
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item >
            </v-list>
        
        </v-navigation-drawer>
    </div>
    
</template>

<script>


export default {
   
    data(){
        return {
            drawer:false,
            links:[
                {icon:'mdi-view-dashboard',text:'Dashboard',route:'/'},
               
                {icon:'mdi-account',text:'About Me',route:'/team'},
            ],
            
           
        }
    }
}
</script>