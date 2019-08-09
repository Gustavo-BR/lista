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
           <v-flex xs10 md4>
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
          <v-flex xs12 md4> 
            <!-- SAVE BUTTON -->
            <v-btn color="green white--text" @click="salvar()">
              <span>SAVE</span>
            </v-btn>

            <!-- MANLIST SETTINGS -->
            <v-btn color="black white--text" 
            @click="statusList=!statusList, showMan=!showMan">
            <span>MAN LIST</span></v-btn>                

            <!-- WOMANLIST SETTINGS -->    
              <v-btn color="white" 
              @click="statusList=!statusList, showWoman=!showWoman">
              <span>WOMAN LIST</span></v-btn>
          </v-flex>
        </v-container>
        
      </v-form>
      <v-spacer></v-spacer>
      <v-list>
        <!-- DATA TABLE OF BOUTH -->
        <v-card>
          <v-data-table
          v-show="statusList"
          :headers="HEADER"
          :items="ListAll"
          class="elevation-1"
          :itens-per-page="20"
          ></v-data-table>
        </v-card>
        <!-- DATA TABLE OF MANS -->
        <v-card>
          <v-data-table
          v-show="showMan"
          :headers="HEADER"
          :items="ManList"
          class="elevation-1"
          :itens-per-page="20"
          ></v-data-table>
        </v-card>
        <!-- DATA TABLE OF WOMANS -->
        <v-card>
          <v-data-table
          v-show="showWoman"
          :headers="HEADER"
          :items="WomanList"
          class="elevation-1"
          :itens-per-page="20"
          ></v-data-table>
        </v-card>
      </v-list>
    </v-content>
  
  </v-app>
</template>


<script>
// DEFAULT OPTIONS
import { defaultCoreCipherList } from 'constants';
  export default {
    data: () => ({
    dialog: false,
    statusList: true,
    showMan: false,
    showWoman: false,
    name: [],
    genre:[],
    HEADER: [
    {
      text: 'Nomes',
      align: 'left',
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
    // DECLARATION OF ARRAYS
    ManList:[],
    WomanList:[],
    ListAll:[],
  }),
  // SAVE FUNCTION TO INSERT NAMES ON LISTS
  methods:{
    salvar(){
      switch(this.genre){
        case 'Man':
          this.ManList.push({name: this.name, genre: this.genre})
          this.ListAll.push({name: this.name, genre: this.genre})
          this.name=""
          this.genre=""
          break;
        case 'Woman':
          this.WomanList.push({name: this.name, genre: this.genre}) 
          this.ListAll.push({name: this.name, genre: this.genre})
          this.name=""
          this.genre=""
          break;
          default:
          break;
      }
    }               
  }
}
</script>