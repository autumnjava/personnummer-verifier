<template>
<div class="wrapper">
  <form @submit.prevent="logIn">
    <input v-model="personNr"/>
    <button :disabled="!input" :class="{active: isActive}">Skapa konto</button>
  </form>
</div>
</template>

<script>
export default {
  name: 'Register',
  data() {
    return {
      personNr: "",
      isActive: false,
    }
  },
  computed:  {
    input()  {
      let regexList = [/^\d{10}$/, /^\d{12}$/, /^\d{6}\-\d{4}$/, /^\d{8}\-\d{4}$/];
      this.isActive = regexList.some(rx => rx.test(this.personNr));
      if(this.isActive){
          this.checkDate(this.personNr);

         //return this.isActive = true ? dateConverter == true : false ;
      }
    },
  },
  methods:{
    logIn(){
      alert("Välkommen in");
    },
    checkDate(personNr){
      if(personNr.length === 13 || this.personNr.length === 12 ){
        if(personNr.substring(0, 2) === '19'  || personNr.substring(0, 2) === '20'){
        let yyyy = personNr.substring(0, 4);
        let mm = personNr.substring (4,6);
        let dd = personNr.substring(6,8);
        console.log(yyyy, mm, dd, 'hey long')
        }
      } else {
        let yy = personNr.substring(0, 2);
        let mm = personNr.substring (2,4);
        let dd = personNr.substring(4,6);
        console.log(yy, mm, dd, 'hey short')
      }
    },
    
  }
}
</script>

<style scoped>
.wrapper{
  margin: 10px 0;
}
form {
  border-radius: 10px;
}

form > input {
  margin: 15px 0;
  display: block;
}

form > button {
  background-color: #22255a;
  border: none;
  color: white;
  padding: 12px 32px;
  text-align: center;
  text-decoration: none;
  width: 100%;
  opacity: 50%;
  cursor: pointer;
  border-radius: 20px;
  font-size: medium;
  font-family: Georgia, 'Times New Roman', Times, serif;
}

.active {
opacity: 100%;
}
</style>
