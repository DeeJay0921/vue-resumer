<template>
  <div id="app" v-bind:class="{activePreview: previewMode}">
    <Topbar class="topbar" v-on:appListenPreview="appDealPreview"></Topbar>
    <main>
      <Editor v-bind:resume="resume" class="editor"></Editor><!--传给editor数据-->
      <Preview v-bind:resume="resume" class="preview"></Preview>
    </main>
    <el-button id="exit" v-on:click="exitPreview">退出预览</el-button>
  </div>
</template>

<script>
  import Topbar from './components/Topbar.vue'
  import Editor from './components/Editor.vue'
  import Preview from './components/Preview.vue'


  export default {
    components: {
      Topbar,Editor,Preview
    },
    data() { //在data()中存放数据，以便editor和preview使用
      return {
        previewMode: false,
        resume: {
          profile: {
            name: '',
            city: '',
            birth: ''
          },
          workExperience: [
            {
              company:'',
              content:''
            }
          ],
          studyExperience: [
            {school:'',duration:'',degree:''}
          ],
          projectExperience: [
            {name: '',content:''}
          ],
          awardExperience: [
            {name: ''}
          ],
          contacts: {
            qq: '',
            wechat: '',
            email:'',
            phone: ''
          }
        }
      }
    },
    methods: {
      appDealPreview() {
        this.previewMode = true;
        console.log(this.previewMode)
      },
      exitPreview() {
        this.previewMode = false;
      }
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
  #exit {
    display: none;
  }
  .activePreview #exit {
    display: inline-block;
    position: fixed;
    right: 2em;
    top: 1em;
  }
  #app main {
    display: flex;
    flex: 1;
    background: rgba(205, 215, 252, 0.81)
  }
  #app main .editor {
    width: 45em;
    margin: 16px 8px 16px 16px;
    background: #fff;
    box-shadow: 0 0 5px rgba(0,0,0,0.5);
    border-radius: 5px;
    overflow: hidden;
  }
  #app main .preview {
    flex: 1;
    margin: 16px 16px 16px 8px;
    background: #fff;
    box-shadow: 0 0 5px rgba(0,0,0,0.5);
    border-radius: 5px;
  }
  .activePreview #topbar {
    display: none;
  }
  .activePreview main #editor {
    display: none;
  }
  .activePreview main #preview {
    max-width: 760px;
    margin: 2em auto;
    overflow: auto;
  }
</style>
