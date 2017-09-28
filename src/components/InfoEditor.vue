<template>
  <div>
    <h2>{{title}}</h2>
    <el-form v-for="(item,index) in keys" v-bind:key='index'>
      <el-form-item v-bind:label="labels[item]">
        <el-input v-model="info[index]"></el-input>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
  export default {
    props: ['info','labels','title'], //允许从外部接收一个profile
    computed: {
      keys() {
        return Object.keys(this.info)
      }
    }
  }
</script>
