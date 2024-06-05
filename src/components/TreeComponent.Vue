<template>
    <v-treeview :items="treeItems" open-all>
      <template v-slot:prepend="{ item }">
        <v-icon v-if="item.children">mdi-folder</v-icon>
        <v-icon v-else>mdi-file</v-icon>
      </template>
      <template v-slot:append="{ item }">
        <v-btn small @click="editItem(item)">Edit</v-btn>
        <v-btn small @click="deleteItem(item)">Delete</v-btn>
      </template>
    </v-treeview>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        treeItems: []
      };
    },
    methods: {
      fetchTreeData() {
        axios.get('/api/tree')
          .then(response => {
            this.treeItems = response.data;
          });
      },
      editItem(item) {
        // logic to edit item
      },
      deleteItem(item) {
        // logic to delete item
      }
    },
    created() {
      this.fetchTreeData();
    }
  };
  </script>
  
  