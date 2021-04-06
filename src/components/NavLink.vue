<template>
    <router-link :to="route.path" class="dry-eraser" tag="div" :class="route.color"
    ><span>{{route.name}}</span></router-link>
</template>

<script>
import EventBus from '../event-bus.js'

export default {
    name: 'NavLink',
    props: ['route'],
    methods: {
        onClick : function(path) {
            this.eraseWhiteboard(path);
        },
        eraseWhiteboard : function() {
            EventBus.$emit('eraseWhiteboard');
        }
    },
    mounted () {
        EventBus.$on('finishedErasingWhiteboard', () => {
            
        })
    }
}
</script>

<style lang="scss">
.dry-eraser{
    height:60px;
    width:20%;
    background-position:top;
    background-size:cover;
    line-height:40px;
    text-align:left;
    padding-left:10%;
    cursor:pointer;
    span{
        text-decoration: none;
        font-weight:bold;
        color:white !important;
    }
}

.red-marker{
    background-image:url('/images/red-marker.svg');
    &.router-link-exact-active{
        background-image:url('/images/red-marker-open.svg');
    }
}

.brown-marker{
    background-image:url('/images/brown-marker.svg');
    &.router-link-exact-active{
        background-image:url('/images/brown-marker-open.svg');
    }
}

.green-marker{
    background-image:url('/images/green-marker.svg');
    &.router-link-exact-active{
        background-image:url('/images/green-marker-open.svg');
    }
}

.blue-marker{
    background-image:url('/images/blue-marker.svg');
    &.router-link-exact-active{
        background-image:url('/images/blue-marker-open.svg');
    }
}

</style>