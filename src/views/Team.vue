<template>
  <div class="Team">
   <h3 class="grey--text">Team</h3>
    <v-container  class="my-5">
     <v-row wrap align="center" justify="center">
       <v-col cols="12" sm="6" md="4" lg="3" v-for="person in team" :key="person.name" >
          <v-card flat class="text-center ma-3" >
            <v-responsive pt-4>
              <v-avatar size="100" class="grey lighten-2">
                <img :src="person.avatar">
              </v-avatar>
            </v-responsive>
            <v-card-text>
              <div class="subheading">{{person.name}} </div>
              <div class="grey--text">{{person.role}}</div> 
            </v-card-text>
            <v-card-action> 
              <v-btn text color="grey">
                <v-icon small left>mdi-message</v-icon>
                <span>Message</span>
              </v-btn>
            </v-card-action>
          </v-card>
       </v-col>
     </v-row>
    </v-container >
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Home',
  data(){
    return{
      team: [
        
        { name: 'Rowan Tamang', role: 'Web Developer',avatar:'/meow.jpg' }
        
      ]


    }
  }
  
}
</script>
