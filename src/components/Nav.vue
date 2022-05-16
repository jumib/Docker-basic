<template>
<v-container fluid class="no-padding" id="header">
  <v-app-bar color="deep-purple accent-4"
      dense class="space">
      <v-toolbar flat class="no-padding" style="margin-top:10px">
          <v-toolbar-title class="logo-img mouse-hover">
              <span onclick="location.href='/'"><v-img contain src="../assets/logo.png"/></span>
          </v-toolbar-title>


          <v-toolbar-items>
            <v-layout align-center>
                <v-btn class="font-top" depressed color="white">채용</v-btn>
                <v-btn class="font-top" depressed color="white">커뮤니티</v-btn>
            </v-layout>
          </v-toolbar-items>



          <v-toolbar-items>
              <v-layout align-center>
                <p :class="{'active':recruitclick}" onclick="location.href='/job/recruit'" @focus="recruitclick = true" @blur="recruitclick = false" class="font-top" style="margin-left:56px">채용</p><br>
                <p :class="{'active':commclick}" onclick="location.href='/community/talk'" @focus="commclick = true" @blur="commclick = false" class="font-top mouse-hover" style="margin-left:32px">커뮤니티</p><br>
              </v-layout>
          </v-toolbar-items>




          <v-spacer></v-spacer>
          <v-text-field solo label="회사, 직종, 포지션 검색" prepend-inner-icon="mdi-magnify" filled dense class="expanding-search mt-5 ml-n16"
                        :class="{'closed':searchClosed && !JobSearch}"
                        @focus="searchClosed = false" @blur="searchClosed = true"
                        v-model="JobSearch" clearable style="margin-right:32px">
          </v-text-field>
          <template v-if="!currentUser">
            <span class="font-top mouse-hover" @click="login">로그인 / 회원가입</span>
          </template>
          <template v-else>
            <span class="font-top mouse-hover" @click="logout">로그아웃</span>
          </template>
      </v-toolbar>
  </v-app-bar>

</v-container>
</template>
<script>

export default {
  data(){
    return{
      searchClosed: true,
      JobSearch: null,
      deviceWidth: 0,
      deviceML: 0,
      recruitclick: false,
      commclick: false
    }
  },
}
</script>

<style>
@media all and (max-width:960px){
  .expanding-search{
    display: none;
  }
}
#header{
  width: 1920px;
  height: 83px;
}
v-toolbar .v-toolbar__content{
  padding:0% !important;
}
.expanding-search::before::after{
  border-color: transparent !important;
}
.expanding-search{
  transition: max-width 0.3s;
}
.expanding-search.closed{
  max-width: 45px;
}
.logo-img{
  margin-top: -5px !important;
  max-width: 118px !important;
}
.v-toolbar__content, .v-toolbar__extension {
  padding:0% !important;
}
.font-top{
  font-weight: 800;
  font-size: 16px;
  line-height: 20px;
  text-align: center;
  letter-spacing: -0.7px;
  color: #2B2B2B;
}
.active{
  box-shadow: inset 0 -3px #33CCCC;
}
.span::after{
  border-bottom: 2px solid #33CCCC;
}
.v-application p {
    margin-bottom: 0px !important;
}
</style>