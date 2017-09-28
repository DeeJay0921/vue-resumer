<template>
  <div>
    <h2>{{title}}</h2>
    <el-form>
      <div v-for="(exp,index) in exps" class="container">
        <el-form-item v-for="key in keys" v-bind:label="labels[key] || key" v-bind:key="key">
          <el-input v-model="exps[key]"></el-input>
        </el-form-item>
        <i class="el-icon-circle-close" v-on:click="removeExp(index)"></i>
      </div>
      <el-button type="primary" v-on:click="addExp()">添加经历</el-button>
    </el-form>
  </div>
</template>
<script>
  export default {
    props: ['exps','labels','title'],
    methods: {
      addExp() {
        const empty = {}
        this.keys.map( (key)=> {
          empty[key] = {}
        })
//        this.exps.push({school:'',duration:'',degree:''})
        this.exps.push(empty)
      },
      removeExp(index) {
        if (this.exps.length === 1 ){
          alert('不能把经历都删除了哦')
          return;
        }
        else {
          this.exps.splice(index,1)
        }
      }
    },
    computed: {
      keys(){
        return Object.keys(this.exps[0]) //进行遍历study所有的key
      }
    }
  }
</script>
