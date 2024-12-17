<template>
  <div class="demo-image">
  <div class="block" v-for="fit in fits" :key="fit">

    <el-image
      style="width: 40px; height: 40px"
      :src="url"
      :fit="fit"></el-image>
  </div>
</div>
</template>

<script>
  export default {
    data() {
      return {
        fits: ['cover'],
        url: require('@/assets/now.png')
      }
    }
  }
</script>
<style scoped>
.el-image{
  margin-left: 20px;
  margin-right: 0px;
}
</style>
