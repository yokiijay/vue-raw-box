<template>
  <div id="app">
    <Box class="container" center>
      <h1>默认位置</h1>
      <Box class="card" size='300px'>
        <pre>{{content1}}</pre>
      </Box>
    </Box>

    <Box class="container" center>
      <h1>→ 居中 ←</h1>
      <Box class="card" size='300px' center>
        <pre>{{content2}}</pre>
      </Box>
    </Box>

    <Box class="container" center>
      <h1>← 水平居左 垂直居中</h1>
      <Box class="card" size='300px' center left>
        <pre>{{content3}}</pre>
      </Box>
    </Box>

    <Box class="container" center>
      <h1>↘ 水平居右 垂直居下</h1>
      <Box class="card" size='300px' center right bottom>
        <pre>{{content4}}</pre>
      </Box>
    </Box>

  </div>
</template>

<script>
import Vue from 'vue';
import Box from 'vue-raw-box'

export default Vue.extend({
  name: 'ServeDev',
  components: {
    Box
  },
  data(){
    return {
      content1:
`<Box
  size="300px"
>
默认位置
</Box>`,
      content2:
`<Box
  size="300px"
  center
>
居中
</Box>`,
      content3:
`<Box
  size="300px"
  center
  left
>
水平居左 垂直居中
</Box>`,
      content4:
`<Box
  size="300px"
  center
  right
  bottom
>
水平居右 垂直居右
</Box>`,
    }
  }
});
</script>

<style scoped>
.container {
  padding: 40px 0;
  border-bottom: 1px solid rgb(238, 238, 238);
}
.container:first-of-type {
  margin-top: 0;
}
.container:last-of-type {
  margin-bottom: 0;
}
.card {
  background: linear-gradient(270deg, #a24bcf, #4b79cf, #4bc5cf);
  background-size: 300%;
  color: white;
  font-size: 16px;
  margin: 10px;
  padding: 10px;
  border-radius: 4px;
  transition: .4s;
}
.card{
    -webkit-animation: AnimationName 30s ease infinite;
    -moz-animation: AnimationName 30s ease infinite;
    animation: AnimationName 30s ease infinite;
}

@-webkit-keyframes AnimationName {
    0%{background-position:0% 50%}
    50%{background-position:100% 50%}
    100%{background-position:0% 50%}
}
@-moz-keyframes AnimationName {
    0%{background-position:0% 50%}
    50%{background-position:100% 50%}
    100%{background-position:0% 50%}
}
@keyframes AnimationName {
    0%{background-position:0% 50%}
    50%{background-position:100% 50%}
    100%{background-position:0% 50%}
}
pre {margin: 0;}
</style>