<template>
  <div>
    <h2>联系方式</h2>
    <el-form>
      <el-form-item label="QQ">
        <el-input v-model="contacts.qq"></el-input>
      </el-form-item>
      <el-form-item label="微信">
        <el-input v-model="contacts.wechat"></el-input>
      </el-form-item>
      <el-form-item label="邮箱">
        <el-input v-model="contacts.email"></el-input>
      </el-form-item>
      <el-form-item label="手机号码">
        <el-input v-model="contacts.phone"></el-input>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
  export default {
    props: ['contacts'], //允许从外部接收一个profile
  }
</script>
