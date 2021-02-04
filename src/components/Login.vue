<template>
<div class="wrapper">
  <div class="left">
    <h2>Har du ett konto?</h2>
      <p>Logga in här
        <img src="../assets/arrow_right_white.svg" />
      </p>
  </div>

  <div class="right">
    
  </div>
</div>
</template>

<script>
//<input required v-model="email" type="email" />
//<p class="failedLogin" v-if="errorMessage">Ogiltig E-post/Lösenord</p>
export default {
  name: 'Login',
  data() {
    return {
    }
  },
  computed:  {
   
  },
  methods:{

  }
}
</script>

<style scoped>
.wrapper {
  width: 100%;
  background: #eee;
  border-radius: 20px;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}

.left{
  width: 250px;
  text-align: left;
  padding: 10px;
  font-size: 20px;
  font-weight: 550;
}

.right{
background: url(../assets/account.svg);
background-repeat: no-repeat;
background-size: 60px 60px;
background-position: center;
}

img {
  background: #22255a;
  border-radius: 10px;
  border: 5px solid #22255a;
  width: 10px;
}

</style>
