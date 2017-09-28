<template>
  <div id="topbar">
    <div class="logo">
      VueResumer
    </div>
    <div class="actions">

      <el-button type="primary" v-on:click="preview">预览</el-button>

    </div>
  </div>
</template>
<script>

  export default {
    methods: {
      preview() {
        this.$emit('appListenPreview')
      }
    },
    data(){
      return {

      }
    }
  }
</script>
<style lang="scss">
  #topbar {
    min-height: 100px;
    display: flex;
    justify-content: space-between;
    padding: 16px;
    font-size: 20px;
    align-items: center;
    .actions button {
      margin-right: 5em;
    }
  }
</style>
