<template>
  <div id="app">
    <input type="text" maxlength="7" v-model="text">
    <button @click="created()">住所自動入力</button>
    <p>Address:{{address}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data(){
    return{
      address:"",
      text:""
    }
  },
  methods:{
    async created(){
      console.log(this.text);
      let item = await axios.get(
      `https://apis.postcode-jp.com/api/v3/postcodes/${this.text}?apikey=Gq4hN0Af636GO5Rlt42CIPsp5vSmMp1re0jDqgR`
      );
      this.data = item.data;
      this.address = this.data.allAddress;
    }
  }
};
</script>

<style>

</style>
