
<template>
    <div class="table-wrapper ">
    <table class="table">
      <thead>
        <tr>
          <th v-for="col in columns" :key="col.key">
            <slot :name="`header-${col.key}`">
              {{ col.label }}
            </slot>
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(row, rowIndex) in rows" :key="rowIndex">
          <td v-for="col in columns" :key="col.key">
            <slot :name="`cell-${col.key}`" :row="row">
              {{ row[col.key] }}
            </slot>
          </td>
        </tr>
      </tbody>
    </table>
</div>
  </template>
  
  <script>
  export default {
    name: 'DataTable',
    props: {
      columns: {
        type: Array,
        required: true
      },
      rows: {
        type: Array,
        required: true
      }
    }
  }
  </script>
  
  <style scoped>
  .table-wrapper {
  display: flex;
  justify-content: center;
  margin-top: 1rem; 
}
.table{
        border: 1px solid #ccc;
        border-radius:5px;
        background-color: #f9f9f9;
        padding: 1rem;
        
    }
 </style>
  