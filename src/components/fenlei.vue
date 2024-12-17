<template>
    <el-menu class="rounded-menu">
        <el-menu-item index="1">全部</el-menu-item>
        <el-menu-item index="2">生活话题</el-menu-item>
        <el-menu-item index="3">校园趣事</el-menu-item>
        <el-menu-item index="4">求助问答</el-menu-item>
        <el-menu-item index="5">资源分享</el-menu-item>
        <el-menu-item index="6">学生活动</el-menu-item>
        <el-menu-item index="7">学习经验分享</el-menu-item>
        <el-menu-item index="8">校园美食</el-menu-item>
        <el-menu-item index="9">校园活动</el-menu-item>
        <el-menu-item index="10">校园趣事</el-menu-item>
        <el-menu-item index="11">校园美食</el-menu-item>
        <el-menu-item index="12">校园活动</el-menu-item>
    </el-menu>
</template>
<script>
export default {
    data() {
        return {
            activeIndex: '1',
        }
    },
  
    name: 'fenlei',
}
</script>

<style scoped>
.rounded-menu {
    border-radius: 8px;
    overflow: hidden;
}

.el-menu-item {
    border-radius: 4px;
    margin: 2px 4px;
}
</style>