<template>
  <div>
    <v-banner>
      <div class="about">
        <div class="header">
          <div class="title">
            <img
              src="https://www.tcsion.com/dotcom/TCSSMB/Login/images/TATA-logo-left.png"
              alt="Tata Logo"
            />
          </div>
        </div>
        <div class="menu-items">
          <v-img
            max-height="150"
            max-width="150"
            src="@/assets/tcsionimg.png"
          ></v-img>
          <div class="items">
            <a id="phoneno" class="fa-solid fa-phone"> 1800 029 6030</a> |
            <v-icon small color="red"> mdi-message-text </v-icon>
            <a id="redtext"> SMS: 'TCSiON' to 16161</a> |
            <v-icon small color="teal darken-2"> mdi-email </v-icon>
            <a id="phoneno"> Email US </a> |
            <i class="fa-solid fa-computer"></i>
            <v-icon small color="orange darken-2">
              mdi-arrow-up-bold-box-outline
            </v-icon>
            <a id="phoneno"> Visit Our Portal </a> |
            <a id="phoneno"> Help Central </a> |
            <v-icon small color="purple darken-2"> mdi-dialpad </v-icon>
            <a id="phoneno"> Language : </a>
            <select name="English">
              <option value="English">English</option>
              <option value="Spanish">Spanish</option>
              <option value="Japanese">Japanese</option>
              <option value="Bahasa">Bahasa</option>
              <option value="Portugese">Portugese</option>
            </select>
          </div>
        </div>
      </div>
    </v-banner>
    <v-container>
      <v-row>
        <v-col cols="5">
          <img src="@/assets/ion-login-banner.jpg" />
          <div id="text-wrapper">
            Experience the <a id="best"> Best </a><br />
            with all new <a id="orange">TCS iON</a>
          </div>
        </v-col>
        <v-col cols="7">
          <v-card max-width="500">
            <v-form ref="form" id="form" @submit.prevent="loginValidation">
              <div class="form-control">
                <label for="email" class="heading"></label>
                <v-text-field
                  label="Email"
                  v-model="email"
                  type="text"
                  id="email"
                ></v-text-field>
                <span v-if="errorEmail">{{ errorEmail }}</span>
              </div>
              <div class="form-control">
                <label for="password" class="heading"></label>
                <v-text-field
                  label="Password"
                  v-model="password"
                  type="password"
                  id="password"
                ></v-text-field>
                <span v-if="errorPassword">{{ errorPassword }}</span>
              </div>

              <v-btn
                depressed
                rounded
                align="center"
                color="primary"
                type="submit"
                >Login</v-btn
              >
            </v-form>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
export default {
  name: "SignIn",
  data() {
    return {
      email: "",
      password: "",
      errorEmail: "",
      errorPassword: "",
    };
  },
  methods: {
    loginValidation() {

      const loginDetails = JSON.parse(localStorage.getItem('data'))   
      //validation for email-------------------------
      if (!this.email) {
        this.errorEmail = "***required this field";
      }
      else {
        this.errorEmail = "";
      }

      //validation for password----------------------
      if (!this.password) {
        this.errorPassword = "***required this field";
      } 
      
      else {
        this.errorPassword="";
      }
      if(this.errorEmail == "" && this.errorPassword==""){
          let loginData = loginDetails.find(check => check.email === this.email);
          if(this.email == loginData.email && this.password == loginData.password){
          this.$router.push('/newdashboard');
        }
      }
      }
    },
    
}
</script>

