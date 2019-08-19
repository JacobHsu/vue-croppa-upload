<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <croppa v-model="croppa"
            placeholder="Select an image or drag here"
            :placeholder-font-size="14">
            <!-- <img slot="placeholder" src="../assets/upload-solid.svg"> -->
            <img crossOrigin="anonymous" src="https://zhanziyang.github.io/vue-croppa/static/500.jpeg"
         slot="initial">
    </croppa>
    <button @click="upload">UPLOAD</button>
    <br>
    <p>Access to image at 'https:///image/fail.jpeg' from origin 'https://cdpn.io' has been blocked by CORS policy: 
    <br>No 'Access-Control-Allow-Origin' header is present on the requested resource.</p>
    <croppa v-model="myCroppa" :style="styleObject"
            placeholder=""
            :placeholder-font-size="14">
            <img crossOrigin="anonymous" slot="initial">
            
            <svg class="icon icon-remove"
              v-if="isShowIconRemove"
              @click="remove()"
              :style="`top: -5px; right: -5px`"
              viewBox="0 0 1024 1024"
              version="1.1"
              xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink"
              :width="20"
              :height="20">
              <path d="M511.921231 0C229.179077 0 0 229.257846 0 512 0 794.702769 229.179077 1024 511.921231 1024 794.781538 1024 1024 794.702769 1024 512 1024 229.257846 794.781538 0 511.921231 0ZM732.041846 650.633846 650.515692 732.081231C650.515692 732.081231 521.491692 593.683692 511.881846 593.683692 502.429538 593.683692 373.366154 732.081231 373.366154 732.081231L291.761231 650.633846C291.761231 650.633846 430.316308 523.500308 430.316308 512.196923 430.316308 500.696615 291.761231 373.523692 291.761231 373.523692L373.366154 291.918769C373.366154 291.918769 503.453538 430.395077 511.881846 430.395077 520.349538 430.395077 650.515692 291.918769 650.515692 291.918769L732.041846 373.523692C732.041846 373.523692 593.447385 502.547692 593.447385 512.196923 593.447385 521.412923 732.041846 650.633846 732.041846 650.633846Z"
                fill="red"></path>
            </svg>
    </croppa>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      myCroppa: {},
      styleObject: {},
      placeholder: '',
      isShowIconRemove: true 
    }
  },
  methods: {
    upload() {
      if (!this.croppa.hasImage()) {
        alert('no image to upload')
        return
      }
      
      this.croppa.generateBlob((blob) => {
        var fd = new FormData()
        fd.append('file', blob, 'filename.jpg')
        fd.append('other', 'blahblahblah')
        // $.ajax({
        //   url: 'http://www.xxx.com/api/upload',
        //   data: fd,
        //   type: 'POST',
        //   processData: false,
        //   contentType: false,
        //   success: function(data) {
        //     alert(data)
        //   }
        // })
      })
    },
    remove() {
      this.uploadIcon = 'https://www.iconsdb.com/icons/preview/green/upload-xxl.png'
      this.styleObject = {
        backgroundImage: `url(${this.uploadIcon})`,
        backgroundRepeat: 'no-repeat',
        backgroundPosition: 'center',
        backgroundSize: 'contain'
      }
      this.isShowIconRemove = false 
    }
  },
  created() {
    this.url = 'https://zhanziyang.github.io/vue-croppa/static/500.jpeg'
    this.styleObject = {
      backgroundImage: `url(${this.url})`,
      backgroundRepeat: 'no-repeat',
      backgroundPosition: 'center',
      backgroundSize: 'contain'
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.croppa-container {
  border: 1px solid grey;
}
</style>
