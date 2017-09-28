<template>
  <div id="preview">
    <!--在preview.vue中接收不到editor.vue中的数据，所以要把数据放在app.vue里面，传给editor，同时preview也能向父组件获取数据-->
    <!--{{profile.name}}-->
    <div class="profile">
      <h2>个人信息</h2>
      <p>{{`姓名：` + resume.profile.name || `输入姓名`}}</p>
      <p>{{`居住地：` + resume.profile.city || `添加您所在的城市`}}</p>
      <p>{{`出生日期：` + resume.profile.birth || `添加您的出生年月`}}</p>
    </div>
    <div class="work" v-if="filter(resume.workExperience).length > 0">
      <h2>工作经历</h2>
      <ul>
        <li v-for="work in filter(resume.workExperience)">
          <p>{{`公司名称：` + work.company}}</p>
          <p>{{`工作内容：` + work.content}}</p>
        </li>
      </ul>
    </div>
    <div class="study" v-if="filter(resume.studyExperience).length > 0">
      <h2>学习经历</h2>
      <ul>
        <li v-for="study in filter(resume.studyExperience)">
          <p>{{`学校：` + study.school}}</p>
          <p>{{`时间：` + study.duration}}</p>
          <p>{{`学位：` + study.degree}}</p>
        </li>
      </ul>
    </div>
    <div v-if="filter(resume.projectExperience).length > 0" class="project">
      <h2>项目经验</h2>
      <ul>
        <li v-for="pro in filter(resume.projectExperience)">
          <p>{{`项目名称：` + pro.name}}</p>
          <p>{{`项目内容：` + pro.content}}</p>
        </li>
      </ul>
    </div>
    <div v-if="filter(resume.awardExperience).length > 0" class="award">
      <h2>获奖情况</h2>
      <ul>
        <li v-for="award in filter(resume.awardExperience)">
          <p>{{`奖项详情：`+award.name}}</p>
        </li>
      </ul>
    </div>
    <div class="contacts">
      <h2>联系方式</h2>
      <p>{{`QQ：` + resume.contacts.qq || `输入QQ`}}</p>
      <p>{{`微信：` + resume.contacts.wechat || `添加您wexin`}}</p>
      <p>{{`邮箱地址：`+resume.contacts.email || `添加您的email`}}</p>
      <p>{{`电话号码：`+resume.contacts.phone || `添加您的phone`}}</p>
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
    padding: 32px;
    text-align: left;
    line-height: 2.5em;
    overflow: auto;
  }
  #preview .profile>h2,.project>h2,.work > h2,.award>h2,.study>h2,.contacts>h2 {
    font-size: 22px;
    border: none;
    padding: 5px;
    border-bottom: 1px solid black;
    color: #6b8afc;
  }
</style>
