<template>
<h2>User's list</h2>
  <div id="app">
    

    <div class="card" v-for="user in users" :key="user.id.value">
      <div class="header">
      <img class="photo card-element" :src="user.picture.thumbnail" alt="photo" />
       <div class="header_name"> {{ user.name.title }}.{{ user.name.first }} {{ user.name.last }}</div> 
      </div>

      <div>
       
        
        
      </div>
    <div class="Address card-element">
    Sex: {{user.gender}}<br>
    Address: {{user.location.country}},{{user.location.city}},{{user.location.street.name}}
    {{user.location.street.number}}
    </div>
	
&phone;: {{user.phone}}<br>
      	
Email: <a href="#">{{ user.email }}</a>
      <div class="card-element">Age: {{user.registered.age}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {},

  data() {
    return {
      users: [],
    };
  },

  mounted() {
    fetch('https://randomuser.me/api/?results=10')
      .then((response) => {
        return response.json();
      })
      .then((data) => {
        console.log(data);
        this.users = data.results;
      });
  },
};
</script>

<style>
#app {
  line-height:1.5;
  width: 1200px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content:center;
  flex-wrap:wrap;
  align-items:center;
  align-content:center;
  
}
.card:hover{
  cursor:pointer;
  transition: 0.3s;
  transform: scale(1.05);
  box-shadow: 4px 3px 7px grey;
}
.card {
  box-shadow: 3px 2px 5px grey;
  margin-left:15px;
  width:250px;
  height:300px;
  padding: 10px 10px 0px;
  border-radius: 9px;
  border:2px solid black;
  margin-bottom: 15px;
}

.photo {
  border: 4px solid black;
  border-radius: 50px;
}
.header{
  display:flex;
  padding: 0px 30px 5px 20px;
  align-items:center;
  justify-content:space-around;
  margin-bottom:10px;
   border-bottom:2px solid black;
}
a{
color:black;
text-decoration:none;
}
</style>

