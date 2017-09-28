<template>
  <div id="preview">
    <!--在preview.vue中接收不到editor.vue中的数据，所以要把数据放在app.vue里面，传给editor，同时preview也能向父组件获取数据-->
    <!--{{profile.name}}-->
    <h1>{{resume.profile.name || `输入姓名`}}</h1>
    <p>{{resume.profile.city || `添加您所在的城市`}}  |  {{resume.profile.birth || `添加您的出生年月`}}</p>
    <div v-if="filter(resume.projectExperience).length > 0">
      <h2>项目经历</h2>
      <ul>
        <li v-for="pro in filter(resume.projectExperience)">
          {{pro.name}}
          {{pro.content}}
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
  export default {
    //接收editor中填写的数据
//    props: ['profile','workExperience','studyExperience','projectExperience','awardExperience','contacts'],
    props: ['resume'],
    methods: {
      isEmpty (obj) { //判断一个对象的value是否为空
        let empty = true;
        for (let key in obj) {
          if (obj[key]) {
            empty = false;
            break;
          }
        }
        return empty
      },
      filter(arr) {
        return arr.filter( (item)=> {return !this.isEmpty(item)} )
      }
    }
  }
</script>
<style>
  #preview {
    min-height: 100px;
  }
</style>
