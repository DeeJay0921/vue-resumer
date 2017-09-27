<template>
  <div>
    <h2>工作经历</h2>
    <el-form>
      <div v-for="(exp,index) in workExperience" class="container">
        <el-form-item label="公司名称">
          <el-input v-model="exp.company"></el-input>
        </el-form-item>
        <el-form-item label="工作内容">
          <el-input v-model="exp.content"></el-input>
        </el-form-item>
        <i class="el-icon-circle-close" v-on:click="removeWorkExperience(index)"></i>
      </div>
      <el-button type="primary" v-on:click="addWorkExperience">添加经历</el-button>
    </el-form>
  </div>
</template>
<script>
  export default {
    props: ['workExperience'],
    methods: {
      addWorkExperience() {
        this.workExperience.push({
          company:'',
          content:''
        })
      },
      removeWorkExperience(index) {
        this.workExperience.splice(index,1)
      }
    }
  }
</script>
