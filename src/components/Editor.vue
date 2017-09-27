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
        <ProfileEditor v-bind:profile="profile"></ProfileEditor>
      </li>
      <li v-bind:class="{active: currentTab === 1}">
        <WorkExperienceEditor v-bind:workExperience="workExperience"></WorkExperienceEditor>
      </li>
      <li v-bind:class="{active: currentTab === 2}">
        <h2>学习经历</h2>
      </li>
      <li v-bind:class="{active: currentTab === 3}">
        <h2>项目经验</h2>
      </li>
      <li v-bind:class="{active: currentTab === 4}">
        <h2>获奖情况</h2>
      </li>
      <li v-bind:class="{active: currentTab === 5}">
        <h2>联系方式</h2>
      </li>
    </ol>
  </div>
</template>
<script>
  import ProfileEditor from './ProfileEditor.vue'
  import WorkExperienceEditor from './WorkExperienceEditor.vue'
  export default {
    components: {
      ProfileEditor,WorkExperienceEditor
    },
    data() {
      return {
        currentTab: 0,
        icons: ['IDcard','work','book','xiangmu','huojiangzuopin','phone'],
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
        ]
      }
    },
    created() {
      console.log(this.profile);
      setTimeout(()=>{
        console.log(this.profile)
      },5000)
    },
    methods: {

    }
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
