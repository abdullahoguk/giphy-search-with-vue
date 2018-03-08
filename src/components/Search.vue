<template>
    <div class="search">
        <input type="text" v-model="query" placeholder="Search for all gifs in Giphy" @keypress.enter="handleSearch">
        <input type="number" v-model="numberOfRes" placeholder="How Many" @keypress.enter="handleSearch">
        <button @click="handleSearch">Search</button>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                query:"",
                numberOfRes:false
            }
        },
        methods:{
            handleSearch(){
                this.$emit("search",this.query, this.numberOfRes);
            }
        }
    }
</script>


<style>
    *{
    margin: 0px;
    padding: 0px;
    }

    .search input{
        padding: 10px 10px 5px 10px;

        border: none;
        border-radius: .1em;
        outline:none;
        flex-grow: 2;
        background-color: rgba(5, 214, 110,0);
        border-bottom: solid 2px rgb(5, 214, 110);
        color: rgb(0, 22, 18);
    }

    .search input:focus{
        border-bottom: solid 2px rgb(3, 175, 89);
    }

    .search input::placeholder { /* Chrome, Firefox, Opera, Safari 10.1+ */
        color: rgb(2, 89, 84);
        opacity: 1; /* Firefox */
        font-size: .85em;
    }

    .search button{
        padding: 10px 10px;
        border: none;
        border-radius: .2em;
        outline: none;
        color: rgb(255, 255, 255);
        background-color: rgb(3, 202, 103);
        margin-left:.25em; 
    }       

    .search button:hover{
        background-color: rgb(29, 196, 112);
    }  
    .search button:active{
        background-color:rgb(28, 208, 118);
    }   
</style>
