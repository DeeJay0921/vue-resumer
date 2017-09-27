<template>
  <div id="app">
    <Topbar class="topbar"></Topbar>
    <main>
      <Editor class="editor"></Editor>
      <Preview class="preview"></Preview>
    </main>
  </div>
</template>

<script>
  import Topbar from './components/Topbar.vue'
  import Editor from './components/Editor.vue'
  import Preview from './components/Preview.vue'

  export default {
    components: {
      Topbar,Editor,Preview
    }
  }
</script>

<style>
  .icon {
    width: 1em; height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }
  /*<!--让app高度为一个屏幕，必须要让其父元素高度都为100%，否则可以使用100vh-->*/
  html,body,#app {
    height: 100%;
    overflow: hidden;
  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;

    display: flex;
    flex-direction: column;
  }
  .topbar {
    box-shadow: 0 0 5px rgba(0,0,0,0.5);
    position: relative;
    z-index: 1;
  }
  main {
    display: flex;
    flex: 1;
    background: rgba(205, 215, 252, 0.81)
  }
  main .editor {
    width: 40em;
    margin: 16px 8px 16px 16px;
    background: #fff;
    box-shadow: 0 0 5px rgba(0,0,0,0.5);
    border-radius: 5px;
    overflow: hidden;
  }
  main .preview {
    flex: 1;
    margin: 16px 16px 16px 8px;
    background: #fff;
    box-shadow: 0 0 5px rgba(0,0,0,0.5);
    border-radius: 5px;
  }
</style>
