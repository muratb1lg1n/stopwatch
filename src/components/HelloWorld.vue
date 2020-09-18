<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div id="app">
      <div class="container">
        <span id="dakikalar">{{gosterdak}}</span>
        <p>Dakika</p>  
      </div>
      <div class="container">
        <span id="ciftnokta">:</span>
      </div>
      <div class="container">
        <span id="saniyeler">{{gostersan}}</span>
        <p>Saniye</p>
      </div>
      <div class="buton">
        <button @click="tikzaman">bas</button>
      </div>
    </div>
  </div>
  
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: () => ({
    gosterdak: 0,
    gostersan: 0,
    alzaman: 0,
  }),
  computed:{
    _san: () => 1000,
    _dak() {return this._san * 60}
  },
 
  methods: {
    tikzaman(){
      const date = new Date();
      const alzaman = date.getTime();
      return alzaman;   
    },
    krono(){
      const gel = this.tikzaman();

      setInterval(() => {
        const date = new Date();
        const now = date.getTime();

        const fark = now - gel;

        this.gostersan = Math.floor(fark / this._san) % 60;
        this.gosterdak = Math.floor(fark / this._dak);
      },1000)
    }
  },
   mounted(){

    this.krono();
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body{
  background-image: url("https://i.pinimg.com/originals/e2/3d/9c/e23d9cb44dd465c75ac4455c81a07a50.jpg");
  
  text-align: center;
  display: flex;
  flex-direction: column;
  
}
#app{
  display: flex;
  justify-content: center;
  padding: 10px;
  position: relative;
  margin-top:  5%;

  
}
p {
  font-family: "Lucida Console", Monaco, monospace;
  padding: 10px;
  font-size: 45px;
  
}
span {
  font-family: "Lucida Console", Monaco, monospace;
  font-size: 65px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
