<template>
    <div id="pokemon">
        <div class="card">
        <div class="card-image">
            <figure>
            <img :src="pokemon.front" alt="Placeholder image">
            </figure>
        </div>
        <div class="card-content">
            <div class="media">
            <div class="media-content">
                <p class="title is-4">{{num}} - {{name | upper}}</p>
                <p class="subtitle is-6">{{pokemon.type}}</p>
            </div>
            </div>

            <div class="content">
            
            </div>
        </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    created: function(){
        axios.get(this.url).then(res => {
            this.pokemon.type = res.data.types[0].type.name;
            this.pokemon.front = res.data.sprites.front_default;
            console.log(this.pokemon);
        })
    },
    data(){
        return{
            pokemon:{
                type: '',
                front:''
            }
        }
    },
    props:{
        num: Number,
        name: String,
        url: String
    },
    filters:{
        upper: function(value){
            var newName = value[0].toUpperCase()+value.slice(1);
            return newName;
        }
    }

}
</script>

<style>
 #pokemon {
     margin-top:1%;
 }
</style>