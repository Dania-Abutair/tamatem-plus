<script>
  import TextField from './components/TextField.vue'
  export default {
    data: () => ({
      form: false,
      inputFields:[
        {
          value:'',
          rules:['required','emailValidation'],
          type:'email',
          label:'Email',
          name:'Email'
        },
        {
          value:'',
          rules:['required'],
          type:'password',
          label:'Password',
          name:'Password'
        }
      ]
    }),
    components:{TextField}
  }
</script>

<template>
  <div class="app-container">
    <div class="login-card">
      <v-form class="login-form" v-model="form" @submit.prevent>
        <img src="https://avatars.githubusercontent.com/u/124091983" alt="Tamatem Plus Logo " class="login-tamatem-logo" width="128" height="128" />
        <!-- If you want to add another text input field you should create new object in (inputFields Array) 
          with these data (value, rules for validation (required, emailValidation), type, label, name) -->
        <TextField 
          v-for="(input,index) in inputFields"
          :key="index"
          :inputField="input"
        >
        </TextField>
        <v-btn 
          class="submit-button"
          type="submit"
        >
          Login
        </v-btn>
      </v-form>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.login-form {
  width: 100%;
  display: flex;
  max-width: 328px;
  flex-direction: column;
  gap:16px
}
.login-tamatem-logo {
  align-self: center;
}
.submit-button{
  background-color: var(--login-button-color);
  color: #FFFFFF;
  align-self: self-end;
  padding: 9px 26px;
  font-size: 14px;
  font-weight:500;
  box-shadow: 0px 3px 6px var(--box-shadow-color);
}
</style>
