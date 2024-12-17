<!-- src/views/Home.vue
 <!--  -->
<template>

    <div id="UserProfile">
        <el-container>

            <!-- 顶部导航栏 -->
            <el-header>
                <!-- <el-menu :default-active="activeIndex2" class="el-menu-demo" mode="horizontal" @select="handleSelect"
                    background-color="#545c64" text-color="#fff" active-text-color="#ffd04b">
                    <el-menu-item index="1">NOW生活论坛</el-menu-item>
                    <el-menu-item index="2">发帖</el-menu-item>
                    <el-menu-item index="3">
                        <router-link to="/UserProfile">个人中心</router-link>
                    </el-menu-item>
                    <el-menu-item index="4">
                        <router-link to="/Login">退出登录</router-link>
                    </el-menu-item>

                    <el-input placeholder="搜索你感兴趣的内容" suffix-icon="el-icon-search" class="search-input"></el-input>

                    <el-dropdown class="user-dropdown">
                        <el-button>
                            <el-avatar :size="30" :src="circleUrl"></el-avatar>
                            <i class="el-icon-arrow-down el-icon--right"></i>
                        </el-button>
                        <el-dropdown-menu slot="dropdown">
                            <el-dropdown-item>个人信息</el-dropdown-item>
                            <el-dropdown-item>退出登录</el-dropdown-item>
                        </el-dropdown-menu>
                    </el-dropdown>
                </el-menu> -->
            <daohang/>
            
            </el-header>
        </el-container>

        <el-input type="text" placeholder="请输入内容" v-model="text" maxlength="10" show-word-limit>
        </el-input>
        <div style="margin: 20px 0;"></div>
        <el-input type="textarea" placeholder="请输入内容" v-model="textarea" maxlength="30" show-word-limit>



        </el-input>
        <el-main style="margin-top: 20px;">
           <qwe/>
        </el-main>

    </div>

</template>
<script>
import qwe from '@/components/qwe.vue';
import daohang from '../components/daohang.vue'


export default {
    components: {
        daohang,
        qwe,  
    },
    data() {
       
        return {

            activeIndex: '1',
            activeIndex2: '1',
            posts: [
                { id: 1, title: '自我介绍', content: '这是我第一次在论坛发帖，大家好！', date: '2023-10-01', likes: 12 },
                { id: 2, title: '校园活动', content: '我们学校即将举办一次运动会，欢迎大家参加！', date: '2023-10-02', likes: 5 },
                { id: 3, title: '学习经验分享', content: '分享一些学习方法，希望对大家有帮助。', date: '2023-10-03', likes: 8 },
            ],
            circleUrl: 'https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png', // 用户头像的 URL
            carouselImages: [
                'src/assets/Hbg1.png', // 替换为你的图片路径
                'src/assets/Hbg2.png',
                'src/assets/Hbg3.png',
                'src/assets/Hbg4.png'
            ],
            chats: [
                { name: 'JAVAScript', message: '大家好！' },
                { name: '技术交流区', message: '这是一个评论...' },
                { name: '求职面试交流', message: '今天的面试很顺利！' },
                { name: '校园美食交流', message: '推荐大家去试试新开的餐厅！' },
                { name: '动物保护协会', message: '我们下周有活动，欢迎参加！' },
            ]
        }
    },
    methods: {
        handleSelect(key, keyPath) {
            console.log(key, keyPath);
        },
        likePost(postId) {
            const post = this.posts.find(p => p.id === postId);
            if (post) {
                post.likes++;
            }
        }
    }
}
</script>
<style scoped>
#Home {
    background-image: linear-gradient(rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0.8)), url(/Users/sjx/my_forum/src/assets/bg.png);
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
}

.search-input {
    width: 300px;
    margin-right: 20px;
}

.post-button {
    margin-right: 20px;
}

.user-dropdown {
    margin-left: auto;
}

.post-card {
    margin-bottom: 20px;
}

.post-header,
.post-footer {
    display: flex;
    justify-content: space-between;
}

.header-content {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 20px;
    /* 添加内边距 */
}

.el-carousel__item h3 {
    color: #475669;
    font-size: 14px;
    opacity: 0.75;
    line-height: 150px;
    margin: 0;
}

.el-carousel__item:nth-child(2n) {
    background-color: #99a9bf;
}

.el-carousel__item:nth-child(2n+1) {
    background-color: #d3dce6;
}

.line {
    height: 1px;
    background-color: #e0e0e0;
    margin: 10px 0;
}

.carousel-image {
    width: 100%;
    /* 使图片宽度适应容器 */
    height: auto;
    /* 保持图片比例 */
}

.chat-input {
    margin-bottom: 10px;
}

.chat-list {
    max-height: 300px;
    /* 限制聊天记录的高度 */
    overflow-y: auto;
    /* 添加滚动条 */
}

.chat-item {
    padding: 5px;
    border-bottom: 1px solid #e0e0e0;
}
</style> -->
