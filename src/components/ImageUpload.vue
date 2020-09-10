<template>
  <div class="image-upload">
    <h3>Upload your image</h3>
    <p>File should be Jpeg, Png...</p>

    <div v-on:click="fileupload()" class="upload-area">

    </div>
  </div>
</template>

<script>
export default {
  name: 'ImageUpload',

   methods: {
     fileupload: function(){
       console.log("Click");
     }
   }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  $upload-background: #f6f8fb;
  $stroke-color: #97bef4;

  .image-upload{
    
    .upload-area{
      height: 400px;
      width: 400px;
      margin: auto;

      background-color: $upload-background;
      border: 2px dashed $stroke-color;
      border-radius: 5%;

      &:hover{
        cursor: crosshair;
      }
    }
  }
</style>
