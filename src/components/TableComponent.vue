<template>
  <v-data-table :headers="headers" :items="items" class="elevation-1">
    <template v-slot:top>
      <v-toolbar flat>
        <v-toolbar-title>Tabla de Entidades</v-toolbar-title>
        <v-divider class="mx-4" inset vertical></v-divider>
        <v-spacer></v-spacer>
        <v-btn color="primary" @click="openDialog">Agregar Entidad</v-btn>
      </v-toolbar>
    </template>
    <template v-slot:item.actions="{ item }">
      <v-icon small @click="editItem(item)">mdi-pencil</v-icon>
      <v-icon small @click="deleteItem(item)">mdi-delete</v-icon>
    </template>
  </v-data-table>
  <!-- Dialog for CRUD operations -->
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      headers: [
        { text: 'ID', value: 'id' },
        { text: 'Nombre', value: 'name' },
        { text: 'Acciones', value: 'actions', sortable: false }
      ],
      items: []
    };
  },
  methods: {
    fetchItems() {
      axios.get('/api/entities')
        .then(response => {
          this.items = response.data;
        });
    },
    openDialog() {
      // logic to open dialog
    },
    editItem(item) {
      // logic to edit item
    },
    deleteItem(item) {
      axios.delete(`/api/entities/${item.id}`)
        .then(() => {
          this.fetchItems();
        });
    }
  },
  created() {
    this.fetchItems();
  }
};
</script>
