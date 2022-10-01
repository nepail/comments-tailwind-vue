<template>
    <main class="p-4 bg-gray-50 min-h-screen">
        <div class="max-w-screen-xl mx-auto bg-white p-8 rounded-lg shadow-2xl">
            <h2 class="text-3xl my-6">評論</h2>
            <CommentsBox></CommentsBox>
            <DividerHorizontal />
            <div v-for="comment in comments" :key="comment.id">
            
                <CommentsItem 
                    :user="comment.user"
                    :avatar="comment.avatar"
                    :time="comment.time"
                    :content="comment.content"
                />

                <ReplayBox v-if="comment.replies">
                    <CommentsItem 
                        v-for="reply in comment.replies"
                        :key="reply.id"
                        :user="reply.user"
                        :avatar="reply.avatar"
                        :time="reply.time"
                        :content="reply.content"
                    />
                </ReplayBox>
            </div>
        </div>
    </main>
</template>

<script setup>
import CommentsBox from './components/CommentsBox.vue';
import DividerHorizontal from './components/DividerHorizontal.vue';
import CommentsItem from './components/CommentsItem.vue';
import ReplayBox from './components/ReplayBox.vue';

import face1 from "./assets/face01.jpg";
import face2 from "./assets/face02.jpg";
import face3 from "./assets/face03.jpg";

const comments = [
    {
        id: 1,
        user: "Jorden Chen",
        avatar: face1,
        time: "2小時之前",
        content: "哇! 這篇文章寫得真是太好啦! 獲得很多的收穫! 希望原PO能夠再接再厲，產出更多更好的文章!",
        replies: [
            {
                id: 2,
                user: "Amber",
                avatar: face2,
                time: "2小時之前",
                content: "Nice!",
            },
            {
                id: 3,
                user: "Jim Lin",
                avatar: face3,
                time: "15分鐘之前",
                content: 
                    "這篇文章不管是質量還是技術面都解釋得相當透徹，是百年難得一見的好文章，從技術上架構來說，這篇文章確實表現得可圈可點!",
            }
        ]
    }
]

</script>

<style>

</style>