<template>
    <div>
        <el-card v-for="post in posts" :key="post.id" class="post-card">
            <div class="post-header">
                <h3>{{ post.title }}</h3>
                <span class="post-date">{{ post.date }}</span>
            </div>
            <div class="post-content">
                <p>{{ post.content }}</p>
            </div>
            <div class="post-footer">
                <el-button size="small" type="text" @click="likePost(post.id)">点赞 {{ post.likes
                    }}</el-button>
                <el-badge :value="1" class="item" type="primary">
                    <el-button size="small">评论</el-button>
                </el-badge>
            </div>
        </el-card>
    </div>
</template>
<script>
export default {
    data() {
        return {
            activeIndex: '1',
            activeIndex2: '1',
            posts: [
                { id: 1, title: '自我介绍', content: '这是我第一次在论坛发帖，大家好！', date: '2023-10-01', likes: 12 },
                { id: 2, title: '校园活动', content: '我们学校即将举办一次运动会，欢迎大家参加！', date: '2023-10-02', likes: 5 },
                { id: 3, title: '学习经验分享', content: '分享一些学习方法，希望对大家有帮助。', date: '2023-10-03', likes: 8 },
                { id: 4, title: '校园美食', content: '推荐大家去试试新开的餐厅！', date: '2023-10-04', likes: 10 },
                { id: 5, title: '校园活动', content: '我们学校即将举办一次运动会，欢迎大家参加！', date: '2023-10-02', likes: 5 },
                { id: 6, title: '学习经验分享', content: '分享一些学习方法，希望对大家有帮助。', date: '2023-10-03', likes: 8 },
                { id: 7, title: '校园美食', content: '推荐大家去试试新开的餐厅！', date: '2023-10-04', likes: 10 },
            ],
        }
    },
    name: 'tiezi',
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
.post-card {
    margin-bottom: 20px;
}
</style>