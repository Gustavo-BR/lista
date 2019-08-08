<template>
  <v-app>
    <!-- HEADER -->
    <v-app-bar app color=blue>
      <v-toolbar-title class="headline text-uppercase">
        <span class="font-weight-light">GUSTAVO'S</span>
        <span >LIST</span>
      </v-toolbar-title>      
    </v-app-bar>

    <v-content>
      <v-form v-model="valid">
        
        <!-- CONTAINER -->
        <v-container grid-list-xl>
         <!-- NAME AND GENRE BOX -->
         <v-layout wrap>
           <!-- INSERT NAME -->
           <v-flex x10 md4>
             <v-text-field v-model="name" label="NAME" required> 
             </v-text-field>
           </v-flex>
            <!-- INSERT GENRE -->
           <v-flex xs2 md4>
             <v-select v-model="genre" :items="items" label="GENRE" required>
             </v-select>
           </v-flex>
         </v-layout>

          <!-- BUTTONS -->
          <v-flex md3> 
            <!-- SAVE BUTTON -->
            <v-btn color="green white--text" @click="salvar()">
              <span>SAVE</span>
            </v-btn>

            <!-- MANLIST SETTINGS -->
            <v-dialog v-model="dialog" fullscreen hide-overlay="dialog-bottom-transition">
              <!-- MANLIST BUTTON -->
              <template v-slot:activator="{on}">
                <v-btn flat small v-on="on">
                  <span>MAN LIST</span>
                </v-btn>
              </template>
                
              <!-- EXIT DIALOG MANLIST -->
              <v-card>
                <v-toolbar dark color="green">
                  <v-btn icon dark @click="dialog = false">
                    <v-icon>X</v-icon>
                  </v-btn>
                </v-toolbar>
              </v-card>
            </v-dialog> 

            <!-- WOMANLIST SETTINGS -->    
            <v-dialog v-model="dialog" fullscreen hide-overlay="dialog-bottom-transition">
              <!-- WOMANLIST BUTTON -->
              <template v-slot:activator="{on}">
                <v-btn flat small v-on="on">
                  <span>WOMAN LIST</span>
                </v-btn>
              </template>

              <!-- EXIT DIALOG WOMANLIST -->
              <v-card>
                <v-toolbar dark color="black">
                  <v-btn icon dark @click="dialog = false">
                    <v-icon>X</v-icon>
                  </v-btn>
                </v-toolbar>
              </v-card>
            </v-dialog> 
          </v-flex>
        </v-container>
      </v-form>
    </v-content>
  </v-app>
</template>

<script>
  export default {
    data: () => ({
    dialog: false,
    name: '',
    genre:'',
    headers: [
    {
      text: 'Nomes',
      align: 'left',
      sortable: false,
      value: 'nome',
    }
    ],
    select: null,
    items: [
          'Man',
          'Woman',
    ],
            
      WomanList:[],
      ManList:[],

      
  }),
  methods:{
    salvar(){
          switch (this.genre) {
            case "Man":
              this.ManList.push({name: this.name}) 
              break;
          
            default:
              break;
          }
              
    }
    },
  }
</script>