<template>
  <div class="preview">
      <div class="gifsContainer">
          <div v-for="gif in gifs" class="gif">
              <img v-bind:src="gif.images.fixed_height.url" alt="">
          </div>
      </div>
  </div>
</template>

<script>
    export default{
        data(){
            return{
                
            }
        },
        props:{
            gifs:{
                required: true
            },
        },

        methods:{

        }
    }
</script>

<style>
*{
  margin: 0px;
  padding: 0px;
}

.preview{
    width: 100%;
    margin-top: 2em;   
}
.gifsContainer{
    display: flex;
    flex-direction: row;
    flex-flow: wrap;
    align-self: center;
    justify-content: space-between;
}

.gif{
    height: 100%;
    margin: .25em;
}
</style>

