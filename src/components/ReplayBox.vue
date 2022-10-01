<template>
    <button 
        class="pt-4 pb-10 text-blue-600"
        :class="[showCommentBox ? 'pb-2' : 'pb-10']"
        @click="showCommentBox = !showCommentBox"
    >回覆</button>
    <CommentBox 
        v-if="showCommentBox" 
        class="mb-4" 
        @submit="
            emit('submit', $event);
            showCommentBox = false;
        "
    />
</template>

<script setup>
    import { ref } from "vue";
    import CommentBox from "./CommentsBox.vue"

    const showCommentBox = ref(false);

    const emit = defineEmits(["submit"])
</script>

<style>

</style>