 <template>
    <div class="position">
    <div class="table-wrapper">
        <h2>Portal component</h2>
        <h6> ceci est un element qui s'affiche en dehors du composant app et s'affiche directement dans le body</h6>
    </div>
</div>
 </template>
 
 <script>
    export default {
        name: 'PortalApp',
    }
 </script>
 
 <style scoped>

 .position{
    display: flex;
  justify-content: center;
 }
 .table-wrapper {
  display: block;
  justify-content: center;
  margin-top: 1rem; 
  border: 2px solid #ccc;
  border-radius: 3px;
  background-color: #f9f9f9;
  text-align: center;
  height: auto;
  width: 50%
}
 </style>