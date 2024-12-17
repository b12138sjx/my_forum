<template>
    <el-aside width="300px">
        <el-card class="post-card">
            <h3>群聊</h3>
            <el-input placeholder="输入你想说的话" class="chat-input"></el-input>
            <el-card class="chat-card" v-for="(chat, index) in chats" :key="index">
                <div class="chat-item">
                    <strong>{{ chat.name }}:</strong> {{ chat.message }}
                </div>
            </el-card>

        </el-card>
    </el-aside>
</template>
<script>
    export default {
        data() {
            return {
                chats: [
                    { name: 'JAVAScript', message: '大家好！' },
                    { name: '技术交流区', message: '这是一个评论...' },
                    { name: '求职面试交流', message: '今天的面试很顺利！' },
                    { name: '校园美食交流', message: '推荐大家去试试新开的餐厅！' },
                    { name: '动物保护协会', message: '我们下周有活动，欢迎参加！' },
                ]
                
            }
        }
    }
</script>
<style scoped>
.chat-input {
    margin-bottom: 10px;
}

.chat-list {
    max-height: 300px; /* 限制聊天记录的高度 */
    overflow-y: auto; /* 添加滚动条 */
}

.chat-item {
    padding: 5px;
    border-bottom: 1px solid #e0e0e0;
}
</style>