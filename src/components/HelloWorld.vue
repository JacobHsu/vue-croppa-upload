<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <croppa v-model="croppa"
            placeholder="Select an image or drag here"
            :placeholder-font-size="14"
    ></croppa>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
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
        $.ajax({
          url: 'http://www.xxx.com/api/upload',
          data: fd,
          type: 'POST',
          processData: false,
          contentType: false,
          success: function(data) {
            alert(data)
          }
        })
      })
    }
  }
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
</style>
