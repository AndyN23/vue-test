<template>
  <div calss="content">
    <h1>Начальная страница</h1>
    <my-button
      @click="showDialog">
      Открыть окно
    </my-button>
    <my-dialog v-model:show="dialogVisible">
    </my-dialog>
  </div>
</template>

<script>
export default {

  data() {
    return{
      dialogVisible: false,
      isPostLoading: false,
    }
  },
  methods: {
    showDialog(){
      this.dialogVisible = true;
    },
  },
}
</script>

<style lang="scss">
*,
*:after,
*:before{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  max-width: 1200px;
  height: 100vh;
  margin: 0 auto;
  background-color: #f9f9f9;
  padding: 20px;
}

h1{
  margin: 20px auto;
}

</style>
