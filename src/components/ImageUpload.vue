<template>
  <div class="image-upload">
    <h3>Upload your image</h3>
    <p>File should be Jpeg, Png...</p>

    <div v-on:click="fileupload()" class="upload-area" v-cloak @drop.prevent="addFile" @dragover.prevent>
      <img src="../assets/image.svg" />
      <p>Drag & Drop your image here</p>
    </div>

    <p>Or</p>
    <div v-on:click="fileupload()" class="btn">Choose a file</div>
  </div>
</template>

<script>
import fileDialog from 'file-dialog'

export default {
  name: 'ImageUpload',

   methods: {
     fileupload: function(event){
       
        // Check for Drag & Drop 
        const needFileDialog = checkDropzone(event);
        if(needFileDialog){
          openFileDialog();
        }
     },
     addFile: function(event){
        let droppedFiles = event.dataTransfer.files;
        console.log(droppedFiles);
     }
   }
}

// Check Drag & Drop
function checkDropzone(){

  return true;
}

// File Dialog
function openFileDialog(){
  fileDialog({ accept: 'image/*' })
    .then(files => {
        // files contains an array of FileList
        console.log(files);
    });
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

  // Imports
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@500&display=swap');

  $background: #FAFAFB;
  $upload-background: #f6f8fb;
  $stroke-color: #97bef4;
  $drop-text-color: #BDBDBD;

  .image-upload{
    background-color: $background;
    box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
    border-radius: 12px;
    width: 800px;
    height: 800px;
    margin: auto;
    padding: 80px 0px;

    h3{
      font-family: 'Poppins';
      font-style: normal;
      font-weight: 500;
      font-size: 18px;
      line-height: 27px;

      /* identical to box height */
      letter-spacing: -0.035em;
    }

    p{
      font-family: 'Poppins';
      font-style: normal;
      font-weight: 500;
      font-size: 12px;
      line-height: 18px;

      /* identical to box height */
      text-align: center;
      letter-spacing: -0.035em;
    }

    .btn{
      background: #2F80ED;
      border-radius: 8px;
      padding: 8px 16px;
      margin: auto;
      color:white;
      display: inline;

      &:hover{
        cursor: pointer;
      }
    }

    .upload-area{
      height: 400px;
      width: 600px;
      margin: auto;

      background-color: $upload-background;
      border: 1px dashed $stroke-color;
      box-sizing: border-box;
      border-radius: 12px;

      &:hover{
        cursor: crosshair;
      }

      img{
        margin: 80px auto ;
      }

      p{
        font-family: 'Poppins';
        font-style: normal;
        font-weight: 500;
        font-size: 18px;
        line-height: 24px;

        /* identical to box height */
        letter-spacing: -0.035em;

        color:$drop-text-color;
      }
    }
  }
</style>
