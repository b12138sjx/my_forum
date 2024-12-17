<!-- src/views/Home.vue -->
<template>

    <div id="Home">
        <el-container>

            <!-- 顶部导航栏 -->
            <el-header>
                <daohang />
            </el-header>

            <div class="block">
                <el-carousel height="200px" style="margin-top: 10px;">
                    <el-carousel-item v-for="(item, index) in carouselImages" :key="index">
                        <img :src="item" alt="CarouselImage" class="carousel-image" />
                    </el-carousel-item>
                </el-carousel>
            </div>



            <el-container>
                <!-- 左侧分类栏 -->
                <el-aside width="300px">
                    <fenlei />
                </el-aside>

                <!-- 右侧内容区域 -->
                <el-main>
                    <h2>最新帖子</h2>
                    <tiezi />
                </el-main>

                <el-aside width="300px">
                    <qunliao />
                </el-aside>
            </el-container>


        </el-container>
        <div>
            <dilan />
        </div>

    </div>

</template>

<script>
import daohang from '../components/daohang.vue'
import qunliao from '../components/qunliao.vue'
import fenlei from '../components/fenlei.vue'
import tiezi from '../components/tiezi.vue'
import dilan from '../components/dilan.vue'
export default {
    components: {
        daohang,
        qunliao,
        fenlei,
        tiezi,
        dilan,
    },
    data() {
        return {
            circleUrl: 'https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png', // 用户头像的 URL
            carouselImages: [
                require('@/assets/Hbg1.png'),
                require('@/assets/Hbg2.png'),
                require('@/assets/Hbg3.png'),
                require('@/assets/Hbg4.png')
            ],
        }
    },

}
</script>
<style scoped>

    * {
    margin: 0;
    padding: 0;
    box-sizing: border-box; 
}

#Home {
    background-image: linear-gradient(rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0.8)), url(/Users/sjx/my_forum/src/assets/bg.png);
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
    padding: 0; 
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
</style>