<template>
  <v-layout row>
    <v-flex xs12 sm6 offset-sm3>
      <v-card>
        <v-toolbar color="indigo" dark>
          <v-toolbar-side-icon></v-toolbar-side-icon>

          <v-toolbar-title>TODO</v-toolbar-title>

          <v-spacer></v-spacer>

          <v-btn icon @click="addItem(title)">
            <v-icon>ADD</v-icon>
          </v-btn>

          <v-btn icon>
            <v-icon>more_vert</v-icon>
          </v-btn>
        </v-toolbar>
        <v-list>
          <input type="text" v-model="title" placeholder="할일을 입력해주세요">
          <v-list-tile
            v-for="(item,index) in items"
            :key="item.title"
            avatar
            @click="deleteItem(index)"
           >

            <v-list-tile-content>
              <v-list-tile-title v-text="item.title"></v-list-tile-title>
            </v-list-tile-content>

          </v-list-tile>
        </v-list>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    data () {
      return {
        title:"",
        items: [
            { title: '운동하기'},
            { title: '밥먹기'},
            { title: '잠자기'},
            { title: '학교오기'},
            ]
      }
    },
    methods:{
      addItem(title){
        if(title=="")return;
        this.items.push({title:title})
        this.title =""
      },
      deleteItem(index){
        this.items.splice(index,1);
      }
    }
  }
</script>