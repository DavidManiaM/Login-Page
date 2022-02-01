<template>
  <div id="box">
    <div id="title">
      <h1>Welcome to the login page!</h1>
      <p>Please, fill in the form with information about your account</p>
    </div>
    <div id="main-content">
      <i class='bx bxl-gmail'></i>
      <label v-bind:class="{blank: !check.email}">Email: </label>
      <input type="text" placeholder="email" required v-model="preInf.email" ref="emailInput" autofocus/><pre style="display: inline-block">           </pre>
      <i class='bx bx-key bx-sm' ></i>
      <label v-bind:class="{blank: !check.pass}">Password: </label>
      <input type="password" placeholder="password" required v-model="preInf.pass" ref="passInput" maxlength="20"/>
    </div>
    <div id="requests">
      <br>
      <label><b>Tell us your experience: </b></label><br><br>
      <textarea cols="30" rows="10" placeholder="Your experience: " maxlength="200"></textarea><br><br>
      <button v-on:click="send">Send</button>
      <p v-if="showThxMsg" id="colorGreen">Thank you for you feedback</p>
      <p v-else id="colorRed" v-if="buttonPressed && !showThxMsg">Please fill the gaps</p>
    </div>
    <div id="infRepeat">
      <p v-if="inf.email"> Your email is: {{inf.email}}</p>
      <p v-if="inf.pass">Your password is: {{inf.pass}}</p>
    </div>
  </div>
</template>

<script>

export default {
  data () {
    return {
      preInf: {
        email: '',
        pass: ''
      },
      inf: {
        email: '',
        pass: ''
      },
      check: {
        email: true,
        pass: true
      },
      showThxMsg: false,
      buttonPressed: false
    }
  },
  methods: {
    send(){
      /*this.inf.email = this.preInf.email;
      this.inf.pass = this.preInf.pass;
      this.showThxMsg = true;*/
      this.buttonPressed = true;
      this.showThxMsg = false;
      if(this.$refs.emailInput.value && this.$refs.passInput.value){
        this.inf.email = this.preInf.email;
        this.inf.pass = this.preInf.pass;
        this.showThxMsg = true;
        this.check.email = true;
        this.check.pass = true;
      }
      else if(this.$refs.emailInput.value){
        if(!this.$refs.passInput.value){
          this.check.pass = false;
        }
        this.check.email = true;
      }
      else if(this.$refs.passInput.value){
        this.check.email = false;
        this.check.pass = true;
      }
      else{
        this.check.email = false;
        this.check.pass = false;
      }
    }
  }
}
</script>

<style>
body{
  background-color: black;
  text-align: center;
}

#box{
  width: 1000px;
  height: 620px;
  margin: 0 auto 0 auto;
  padding: 0;
  /*border: 1px solid lavender;*/
  background-color: white;
  border-radius: 6px;
  box-shadow: 2px 2px 4px 3px white;
}

#title{
  height: 100px;
  width: 100%;
  /*border: 1px solid black;*/
  border-radius: 6px;
  margin: 0;
  padding: 0 0 10px 0;
  background: linear-gradient(dimgrey, white);
  text-align: center;
  /*background-color: dimgrey;*/
}

#title p{
  font-size: 20px;
}

div{
  display: inline-block;
}

#main-content{
  width: 100%;
  height: 50px;
  /*text-align: left;*/
  margin: 10px 0 0 0;
  padding: 10px 0 0 10px;
  border: 1px solid black;
  border-radius: 6px;
  text-align: center;
}

#main-content label{
  font-size: 30px;
  padding-top: 40px;
}

.blank{
  color: red;
  transition: 0.2s;
}

#main-content input{
  height: 20px;
  padding: 0;
}

#requests{
  width: 100%;
  height: 340px;
  border: 1px solid black;
}

#requests label{
  font-size: 20px;
 }

#requests #colorGreen{
  color: lightgreen;
}
#requests #colorRed{
  color: red;
}

#requests textarea{
  width: 300px;
  height: 150px;
  max-width: 400px;
  min-width: 60px;
  max-height: 150px;
  min-height: 40px;
}

#requests p{
  color: lightgreen;
  font-size: 19px;
}

#requests button{
  width: 100px;
  height: 40px;
  font-size: 24px;
  /*margin: auto;*/
}

button:hover{
  cursor: pointer;
}

#infRepeat p{
  font-size: 20px;
}

</style>
