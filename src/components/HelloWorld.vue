<!-- <template>
  <div>
    <input type="file" ref="fileInput" @change="uploadFile" />
  </div>
</template>

<script>
export default {
  methods: {
    uploadFile() {
      const fileInput = this.$refs.fileInput;
      const file = fileInput.files[0];
      
      const formData = new FormData();
      formData.append('file', file);
      
      // Make a POST request to your Django API endpoint
      fetch('http://172.17.17.198:8000/', {
        method: 'POST',
        body: formData,
      })
      .then(response => response.json())
      .then(data => {
        console.log(data);
      })
      .catch(error => {
        console.error('Error:', error);
      });
    }
  }
};
</script> -->


<template>
  <div class="hello">
    <h1>{{ name }}</h1>
    <p>Capital: {{ capital }}</p>
  </div>
</template>

<script>
export default {
 name: 'HelloWorld',
 data() {
  return {
   name: '',
   capital: '',
  };
 },

 async mounted() {
  let query = `{
  allTwittersettings{
    Account
  }
}`;

    try {
   let res = await fetch('http://172.17.17.198:8000/API', {
    method: 'POST',
    headers: {
     'content-type': 'application/json',
    },
    body: JSON.stringify({ query }),
   });
   res = await res.json();
   const response = res.data.allTwittersettings;
   this.name = response.Account;
   this.capital = res;
  } catch (error) {
   console.log(error);
  }
 },
};
</script>

