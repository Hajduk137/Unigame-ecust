<template>
    <ContentBase>
      <div class="row justify-content-md-center">
        <div class="col-3">
          <form @submit.prevent="login">
            <div class="mb-3">
              <label for="exampleInputEmail1" class="form-label">用户名</label>
              <input v-model="username" type="text" class="form-control" id="username" >
        
            </div>
            <div class="mb-3">
                <label for="password" class="form-label">密码</label>
                <input v-model="password" type="password" class="form-control" id="exampleInputPassword1">
            </div>
            <div class="mb-3 form-check">
              <input type="checkbox" class="form-check-input" id="exampleCheck1">
              <label class="form-check-label" for="exampleCheck1">Check me out</label>
            </div>
            <div class="errormessage">{{ error_message }}</div>
            <button type="submit" class="btn btn-primary">登录</button>
        </form>
        </div>
      </div>
    
    </ContentBase>
  </template>
  
  <script>
  import ContentBase from '@/components/ContentBase.vue';  


  import { ref } from 'vue';
  import { useStore } from 'vuex';
  export default {
    name: 'LoginView',
    components: {
        ContentBase,
     
    },//template区域会用到哪些组件
    setup() {
      const store = useStore();
      let username = ref('');
      let password = ref('');
      let error_message = ref('');
      const login = () => {
          store.dispatch("login", {
          username: username.value,
          password: password.value,
          success() {
            console.log("success");
          },
          error() {
            console.log("failed");
          }
          
        });
      };
      return{
        username,
        password,
        error_message,
        login,
      }
    }
  }
  </script>
  
  <style scoped>

  button {
    width:100%;
  }
  .errormessage{
    color: crimson;
  }
  
  </style>
  