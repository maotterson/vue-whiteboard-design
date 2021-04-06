<template>
<v-app>
  <v-container fluid>
    <v-row>
        <v-col xl="2">
        </v-col>
        <v-col xl="8">
          <Nav />
          <v-sheet class="center whiteboard"
            color="white"
            elevation="10"
            height="80vh"
            id="whiteboard"
          >
            <transition name="erase" mode="out-in">
              <router-view/>
            </transition>
          </v-sheet>
        </v-col>
        <v-col xl="2">
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
import Nav from './components/Nav'
import EventBus from './event-bus.js'

export default {
	components: {
		Nav
	},
  mounted () {
    EventBus.$on('eraseWhiteboard', () => {
      document.getElementById('whiteboard').children[0].innerHTML=""
      console.log("erasing whiteboard");
      setTimeout(
        ()=>{
          console.log("whiteboard erased")
          EventBus.$emit('finishedErasingWhiteboard');
        },500)
    });
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color:rgb(252, 251, 240);
}

.whiteboard{
  font-family: 'Sriracha', cursive;
  text-align:left;
  padding:5%;
  h1{
    margin-top:25%;
    font-size:3rem !important;
    animation: write 4s steps(60, end);
    overflow: hidden;
    width:100%;
  }
  p{
    font-size:2rem !important; 
  }
  @keyframes write{ 
    from { width: 0; } 
  } 

  .erase-leave-active{
    filter:blur(100px);
    opacity:0;
  }

  .erase-leave-active{
    transition: 0.5s filter linear, 1s opacity linear;
    -webkit-transition: 1s -webkit-filter linear, 1s opacity linear;
    -moz-transition: 1s -moz-filter linear, 1s opacity linear;
    -ms-transition: 1s -ms-filter linear, 1s opacity linear;
    -o-transition: 1s -o-filter linear, 1s opacity linear;
  }
}


</style>
