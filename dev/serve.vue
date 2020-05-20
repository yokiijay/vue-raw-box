<template>
  <div id="app">
    <Box size='300px'  center row bottom :right="right">
      <h1>Hello Box</h1>
      <!-- <p>Nice to meet you box</p> -->
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
      right: true
    }
  }
});
</script>

<style scoped>
.box {
  background: tomato;
  color: white;
}
</style>