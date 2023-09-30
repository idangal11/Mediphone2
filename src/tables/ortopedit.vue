<template>
    <div class="container">
      <table>
        <thead>
          <tr>
            <th v-for="index in 16" :key="index">{{ index }}</th>
          </tr>
        </thead>
        <tbody>
          <!-- Add table rows and data as required here -->
          <tr>
            <td v-for="index in 16" :key="index">Data {{ index }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    name: 'OrtopEdit'
  };
  </script>
  
  <style scoped>
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
  
  table {
    width: 100%;
    border-collapse: collapse;
  }
  
  th, td {
    border: 1px solid #000;
    padding: 8px 12px;
    text-align: center;
  }
  
  th {
    background-color: #f4f4f4;
  }
  </style>
  