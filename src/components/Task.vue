<template>
  <div>
    <button id="btn" v-on:click="getlistData">LIST ALL DATAS</button><br/>
    <br/>
    <input placeholder="enter id" v-model="uid" /><br /><br />
    <!-- <input type="button" value="Search" @click="getUserdata()" /> -->
    <button id="searchbtn"  @click="getUserdata()">SUBMIT</button>
      <ul>
      <table id="table">
      <tr v-for="item in listData" :key="item.id">
       <td> {{ item.id }}</td>
       <td> {{ item.name }}</td>
       <td>  {{ item.email }}</td>
       <td> {{ item.gender }}</td>
       <td> {{ item.status }}</td>
      </tr>
       </table>
   </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      listData: [],
      uid: "",
    };
  },
  methods: {
    getlistData() {
      fetch("https://gorest.co.in/public/v2/users")
        .then((response) => response.json())
        .then((data) => {
          this.listData = data;
        });
        },
    getUserdata() {
      fetch("https://gorest.co.in/public/v2/users/" + this.uid)
        .then((response) => response.json())
        .then((data) => {
          this.listData = [data];
        });
        },
  },
};
</script>
<style>
li {
  list-style: none;
}
#btn{
background-color: #699ba4; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 30px;
}
input {
  width: 30%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
}
#searchbtn{
  background-color: #e9b098; /* Green */
  border: none;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 10px;
}
#table{
    border: 2px solid black;
   margin-left: auto;
  margin-right: auto;
  ;text-align:center
}
</style>