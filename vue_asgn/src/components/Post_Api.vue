<template>
 
    <div class="main">
      <label for="userid">Email</label>
      <input type="text" name="email" placeholder="email" v-model="email" />
      <br>
      <label for="password">Password</label>
      <input type="password" name="password" placeholder="password" v-model="password" />
      <button @click="addUser()">Login</button>
      <button @click="getPost()">Get Data </button>
    </div>
    
  </template>
  <script>
  
  import axios from 'axios';
  import setAuthHeader from '@/utils/setAuthHeader';

  export default {
    name: "post_api",
    data() {
      return {
        email: "",
        password: "",
     
      };
    },
    methods: {
      addUser() {
         let result = axios.post("https://dev.icc-health.com/dev/login",  {
          email: this.email,
          password: this.password,
        }) 
        .then((response) =>{
            localStorage.setItem('jwtToken',response.data.token);
            setAuthHeader(response.data.token);
        })
        .catch((err) => console.log(err.response));
        console.warn('result', result) 
       
      },
      getPost(){
        axios
        .get("https://dev.icc-health.com/dev/patient?search=crystalo@icc-health.com&orderBy=DESC&orderField=lastMessageSent&filter=WNL&page=2&isActive=1&fromDate=1665990335&toDate=1666854335"
        )
        .then((response) => console.log(response.data))
        .catch((err) => console.log(err.response));
      },
    },
  }
  </script>
  <style>
  h1{
      color: #fff;
  }
  .main{
      margin-left: 35%;
      width: 30%;
      height: 50%;
      background: red;
      overflow: hidden;
      background: linear-gradient(to bottom, #0f0c29, #302b63, #24243e);	border-radius: 10px;
      box-shadow: 5px 20px 50px #000;
  }
  #chk{
      display: none;
  }
  .signup{
      position: relative;
      width:100%;
      height: 100%;
  }
  label{
      color: #fff;
      font-size: 2.3em;
      justify-content: center;
      font-weight: bold;
      cursor: pointer;
     
  }
  input{
      background: #e0dede;
      justify-content: center;
      display: flex;
      margin: 20px auto;
      padding: 10px;
      border: none;
      outline: none;
      border-radius: 5px;
  }
  button{
  
      height: 40px;
      justify-content: center;
      color: #fff;
      background: #573b8a;
      font-size: 1em;
      font-weight: bold;
      margin-top: 20px;
      outline: none;
      border: none;
      border-radius: 5px;
  
  }
  button:hover{
      background: #6d44b8;
  }
  .login{
      height: 460px;
      background: #eee;
      border-radius: 60% / 10%;
      transform: translateY(-180px);
      transition: .8s ease-in-out;
  }
  .login label{
      color: #573b8a;
      transform: scale(.6);
  }
  
  #chk:checked ~ .login{
      transform: translateY(-500px);
  }
  #chk:checked ~ .login label{
      transform: scale(1);	
  }
  #chk:checked ~ .signup label{
      transform: scale(.6);
  }</style>