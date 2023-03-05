<template>
<div class="card edit-field">
    <div class="card-body">
       <label for="edit-post" class="form-label">说点什么</label>
            <textarea v-model="content" class="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
            <button @click="post_a_post" type="button" class="btn btn-primary btn-sm">发送</button>

    </div>
</div>

</template>

<script>
import { ref } from 'vue';

export default {
    name:"UserProfileWrite",
    setup(props, context) {
        let content = ref('');

        const post_a_post = () => {
            context.emit('post_a_post', content.value)
            content.value = "";

        };

        return {
            post_a_post,
            content,
        }
    }
}
</script>


<style scoped>
.edit-field{
    margin-top: 10px;
}
button{
    margin-top: 10px;
}
</style>