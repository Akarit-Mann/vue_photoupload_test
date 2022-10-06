<template>
  <div class="home">
    <div class="imagePreviewWrapper" :style="{'background-image':`url(${previewImage})`}" @click="selectImage"></div>
    <input ref="fileInput" type="file" @change="pickFile">
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      previewImage:[],
    }
  },
  methods: {
    pickFile(){
      let resultss = this.$refs.fileInput.files[0]; 
      if(resultss){

        let reader = new FileReader;
        reader.onload = e => {
          this.previewImage = e.target.result;
          console.log("work");
        }
        reader.readAsDataURL(resultss);
      }
    }
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.imagePreviewWrapper{
    width: 250px;
    height: 250px;
    display: block;
    margin: 0 auto 30px;
    cursor: pointer;
    background-size: cover;
    background-position: center center;
  }
</style>
