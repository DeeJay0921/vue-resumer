<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="i in [0,1,2,3,4,5]"
            v-bind:class="{active: currentTab === i}"
            v-on:click="currentTab = i">
          <svg class="icon">
            <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
          </svg>
        </li>
      </ol>
    </nav>
    <ol class="panes">
      <li v-bind:class="{active: currentTab === 0}">
        <ProfileEditor v-bind:profile="resume.profile"></ProfileEditor>
      </li>
      <li v-bind:class="{active: currentTab === 1}">
        <ExpEditor v-bind:exps="resume.workExperience" v-bind:labels="{company:'公司名称',content:'工作内容'}" v-bind:title="`工作经历`"></ExpEditor>
      </li>
      <li v-bind:class="{active: currentTab === 2}">
        <ExpEditor v-bind:exps="resume.studyExperience" v-bind:labels="{school:'学校',duration:'时间',degree:'学位'}" v-bind:title="`学习经历`"></ExpEditor>
      </li>
      <li v-bind:class="{active: currentTab === 3}">
        <ExpEditor v-bind:exps="resume.projectExperience" v-bind:labels="{name:'项目名称',content:'项目内容'}" v-bind:title="`项目经验`"></ExpEditor>
      </li>
      <li v-bind:class="{active: currentTab === 4}">
        <ExpEditor v-bind:exps="resume.awardExperience" v-bind:labels="{name:'奖励详情'}" v-bind:title="`获奖情况`"></ExpEditor>
      </li>
      <li v-bind:class="{active: currentTab === 5}">
        <ContactsEditor v-bind:contacts="resume.contacts"></ContactsEditor>
      </li>

    </ol>
  </div>
</template>
<script>
  import ProfileEditor from './ProfileEditor.vue'
  import ExpEditor from './ExpEditor.vue'
  import ContactsEditor from './ContactsEditor.vue'
  export default {
    components: {
      ProfileEditor,ExpEditor,ContactsEditor
    },
    props: ['resume'],
    data() {
      return {
        currentTab: 0,
        icons: ['IDcard','work','book','xiangmu','huojiangzuopin','phone'],
      }
    },
    methods: {

    },
  }
</script>

<style lang="scss">
  #editor {
    min-height: 100px;
    display: flex;
    > nav {
      background: black;
      width: 80px;
    }
    > nav > ol > li {
      padding: 16px 0;
      text-align: center;
    }
    > nav > ol > li > .icon {
          width: 24px;
          height: 24px;
          fill: white;
    }
      & > nav  .active {
          transition: all .8s;
          background: white;
        > .icon {
            fill: black;
          }
       }
      > .panes {
        flex: 1;
        .container {
          position: relative;
        }
        .container .el-icon-circle-close {
          position: absolute;
          right: 0;
          top: 0;
        }
           li {
              display: none;
              padding: 32px;
             max-height: 100%;
             overflow: auto;
            }
        }
    & .panes .active {
        display: block;
      }
  }
</style>
