<template>
  <div id="nav">
    <NavLink 
      v-for="route in routes" 
      :key="route.name" 
      :route="route"
    />
  </div>
</template>

<script>
import NavLink from '../components/NavLink'
export default {
	components: {
    NavLink
	},
  name: 'Nav',
  data: function () {
    return {
        routes : [
          { 
            name : "Home",
            path : "/",
            color : "brown-marker"
          },
          { 
            name : "About",
            path : "/About",
            color : "red-marker"
          },
          { 
            name : "Portfolio",
            path : "/Portfolio",
            color : "blue-marker"
          },
          { 
            name : "Contact",
            path : "/Contact",
            color : "green-marker"
          },
        ]
    }
  }
}
</script>

<style lang="scss">
.input {
  width: 100%;
  padding: 8px 10px;
}

#nav {
  padding: 30px;
  display:flex;
  flex-direction: row;
  justify-content: space-evenly;
}

</style>
