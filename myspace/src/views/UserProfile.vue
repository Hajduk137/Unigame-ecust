<template>
    <ContentBase>
        <div class="row">
            <div class="col-3">
                <UserProfileInfo @follow ="follow" @unfollow="unfollow" :user="user"/>
                <UserProfileWrite  @post_a_post="post_a_post"  />    
                
            </div>
                

               
            <div class="col-9">
                <UserProfilePost :posts="posts" />
            </div>
        </div>
    </ContentBase>
  </template>
  
  <script>
  import ContentBase from '../components/ContentBase';  
  import UserProfileInfo from '../components/UserProfileInfo';
  import UserProfilePost from '../components/UserProfilePost';
  import UserProfileWrite from '../components/UserProfileWrite';
  import {reactive} from 'vue';
  import { useRoute } from 'vue-router';
  export default {
    name: 'UserProfile',
    components: {
        ContentBase,
        UserProfileInfo,
        UserProfilePost,
        UserProfileWrite
    },//template区域会用到哪些组件
    setup() {
        const route = useRoute();
        const userId = route.params.userId;
        console.log(userId);
       const user = reactive({
        id: 1,
        username: "hajduk",
        lastname:"li",
        firstname:"an",
        followercount:0,
        is_followed:false,
       });
       const follow = () => {
        if (user.is_followed) return;
        user.is_followed = true;
        user.followercount ++;

       };
       const unfollow = () => {
        if (!user.is_followed) return;
        user.is_followed=false;
        user.followercount --;
       };

       const posts = reactive({
        count: 3,
        posts:[
            {
                id: 1,
                userId:1,
                content:"hello"
            },
            {
                id: 2,
                userId:1,
                content:"test"
            },
            {
                id: 3,
                userId:1,
                content:"good job"
            }
        ]
       })

       const post_a_post = (content) => {
            posts.count ++;
            posts.posts.unshift({
                id: posts.count,
                userId: 1,
                content: content,
            });
       }
       return {
        user,
        follow,
        unfollow,
        posts,
        post_a_post
        
       }
    }
  }
  </script>
  
  <style scoped>
  
  
  </style>
  