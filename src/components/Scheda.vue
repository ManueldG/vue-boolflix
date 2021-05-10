<template>
   <div id="scheda" >
                    
            <li>
                {{lista.title}}
                {{lista.original_title}}
                {{lista.original_language}}
                <img v-if="lista.original_language=='en'" src="img/en.png" alt="en">
                <img v-if="lista.original_language=='it'" src="img/it.png" alt="it">
                <div v-if="lista.original_language!='en'||'it'">{{lista.original_language}}</div>
                {{lista.vote_average}}
                <div class="barra" :style="'width:'+(lista.vote_average*10)+'%'"></div>
                
            </li>       
       

   </div>
</template>

<script>
export default {
    name:'Scheda',
    data(){
        return{
            
        }

    },
    props:{
        lista:Object,
    }

}
</script>

<style>
:root{
    --largh: 1%;
}

img{
    width: 50px;
}
.barra{
    
    height: 5px;
    background-color: yellow;
    border: 1px solid green;

}

</style>