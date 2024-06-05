<template>
  <v-file-input label="Subir PDF" @change="uploadFile" accept=".pdf"></v-file-input>
</template>

<script>
import axios from 'axios';

export default {
  methods: {
    uploadFile(event) {
      const formData = new FormData();
      formData.append('file', event.target.files[0]);
      axios.post('/api/file/upload', formData)
        .then(response => {
          console.log(response.data);
        });
    }
  }
};
</script>
