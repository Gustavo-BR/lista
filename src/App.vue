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
          <v-flex xs12 md3> 
            <!-- SAVE BUTTON -->
            <v-btn color="green white--text" @click="salvar()">
              <span>SAVE</span>
            </v-btn>

            <!-- MANLIST SETTINGS -->
            <v-btn color="blue white--text"><span>MAN LIST</span></v-btn>                

            <!-- WOMANLIST SETTINGS -->    
              <v-btn color="pink white--text"><span>WOMAN LIST</span></v-btn>
          </v-flex>
        </v-container>
        
      </v-form>
      <v-spacer></v-spacer>
        {{ManList[0]}}
        <v-list>
          <v-card>
            <v-data-table
            :headers="HEADER"
            :items="ManList, WomanList"
            class="elevation-1"
            :itens-per-page="20"
            ></v-data-table>
          </v-card>
        </v-list>
      </v-card>
    </v-content>
  
  </v-app>
</template>


<script>
  export default {
    data: () => ({
    dialog: false,
    name: [],
    genre:[],
    HEADER: [
    {
      text: 'Nomes',
      align: 'center',
      sortable: false,
      value: 'name',
    },
    {text: 'Genre', value: 'genre'}
    ],
    select: null,
    items: [
          'Man',
          'Woman',
    ],
            

    ManList:[],
    WomanList:[],

      
  }),
  methods:{
    salvar(){
      this.ManList.push({name: this.name, genre: this.genre}) 
      }
      
              
    }
  }
</script>