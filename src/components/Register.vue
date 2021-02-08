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
      monthLength: [ 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 ],
      currentYear: new Date().getFullYear()
    }
  },
  computed:  {
    input()  {
      let regexList = [/^\d{6}\-?\d{4}$/, /^\d{8}\-?\d{4}$/];
      this.isActive = regexList.some(rx => rx.test(this.personNr));
      if(this.isActive)
         return this.isActive = true ? this.convertToDate(this.personNr) : false;
    },
  }, //end of computed
  methods:{
    logIn(){
      alert("Välkommen in");
    },
    convertToDate(personNr){
      if(personNr.length === 13 || this.personNr.length === 12 ){
        let yyyy = personNr.substring(0, 4);
        let mm = personNr.substring (4,6);
        let dd = personNr.substring(6,8);

        return this.checkDate(yyyy, mm, dd)
      } else {
        let yyyy = 19 + personNr.substring(0, 2);
        let mm = personNr.substring (2,4);
        let dd = personNr.substring(4,6);
        
        return this.checkDate(yyyy, mm, dd)
      }
    },

    checkDate(yyyy, mm, dd){
      if(yyyy < this.currentYear - 150 || mm == 0 || mm > 12)
          return false;

        // Adjust for leap years
        if(yyyy % 400 == 0 || (yyyy % 100 != 0 && yyyy % 4 == 0))
        this.monthLength[1] = 29;

        //extra check to see if the date is in the future
        let date = new Date(yyyy, mm-1, dd)
        let today = Date.now();
        if(date > today)
        return false;

        // Check the range of the day
        return dd > 0 && dd <= this.monthLength[mm - 1];
    }
  } //end of methods
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
