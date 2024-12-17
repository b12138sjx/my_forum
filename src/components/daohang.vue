<template>
    <el-header>
        <el-menu :default-active="activeIndex2" class="el-menu" mode="horizontal" @select="handleSelect"
            background-color="#232E4A" text-color="#fff" active-text-color="#ffd04b">
            <pic />
            <el-menu-item index="1">
                <router-link to="/Home">NOW生活论坛</router-link>
            </el-menu-item>
            <span style="margin:330px;"></span>
            <el-menu-item index="2">
                <router-link to="/Post">发帖</router-link>
            </el-menu-item>


            <el-input placeholder="搜索你感兴趣的内容" suffix-icon="el-icon-search" class="search-input"></el-input>

            <span style="margin:20px;"></span>
            <el-avatar :size="40" :src="circleUrl"></el-avatar>
           
            <el-menu-item index="3">
                <router-link to="/UserProfile">个人中心</router-link>
            </el-menu-item>
            <el-menu-item index="4">
                <router-link to="/Login">退出登录</router-link>
            </el-menu-item>
        </el-menu>
    </el-header>
</template>

<script>
import pic from './pic.vue';
export default {
    data() {
        return {
            count: 0
        }
    },
    components: {
        pic
    }
}
</script>

<style scoped>
.el-header {
    padding: 0 !important;
    margin: 0 !important;
    width: 100vw; /* 设置宽度为视口宽度 */
    position: relative; /* 确保定位正确 */
    left: 50%; /* 向右移动50% */
    transform: translateX(-50%); /* 向左移动自身宽度的一半 */
   
}

.el-menu {
    height: 80px !important;
    margin: 0 !important;
    width: 100% !important;
    display: flex;
    align-items: center;
    border: none !important; /* 去掉白边 */
 
}

.user-pic {
    align-items: center;
}

.search-input {
    width: 200px;
    margin-left: 20px;
}

.el-menu-item {
    margin: 0px;
}

</style>