<template>
   
                    
            <li id="scheda"  :style="cssVars">
                <div class="lato-a">
                    <div class="titolo">Titolo:{{lista.title||lista.name}}</div>
                    <div class="originale">Titolo Originale: {{lista.original_title}}</div>
                    <div v-if="lista.original_language=='en'"><img  src="img/en.png" alt="en"></div>
                    <div v-else-if="lista.original_language=='it'"><img  src="img/it.png" alt="it"></div>
                    <div v-else>{{lista.original_language}}</div>
                    {{lista.vote_average}}
                    <div class="vote">
                        <div class="stars" :style="cssVars">
                            <span class="material-icons-two-tone">
                            star star star star star
                            </span>
                            
                        </div>
                        <!--<div class="barra" :style="cssVars" ></div> :style="'width:'+(lista.vote_average*10)+'%'"-->
                    </div>  
                    <div class="overview">{{lista.overview}}</div>  
                </div>
                <div class="lato-b">                    
                    <img :src="'https://image.tmdb.org/t/p/w500'+lista.poster_path" alt="en">
                    
                </div>
                
            </li>       
       

   
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
    },
    methods:{
        five2ten(val){  
            return (Math.floor(((val/10)*(5-0)+0)));  
        }
    },
    computed:{
        cssVars(){
            return{
                '--voto-medio': (this.five2ten(this.lista.vote_average)*20)+'%',
                '--sfondo-scheda': 'greenyellow'
            };
        }
    }

}
</script>

<style scoped lang="scss">

@import "@/scss/vars";

li#scheda{
    position:relative;
    width: $width-card;
    height: $height-card;
    margin: $margin-card;
    list-style: none;
    text-overflow: ellipsis;
    

    .lato-a{  
        position:absolute; 
        box-sizing: border-box;
        width: $width-card;
        height: $height-card;
        border: 1px solid green;
        border-radius: 5px;        
        margin: 0;
        padding: 20px;
        top: 0;
        background-color: #019ff9;
        background-image: linear-gradient(to bottom, #019ff9, #83cffa);
        z-index:1;
        overflow: auto;
        transition: transform 2s , z-index 2s;
        
        .overview{
            height: calc(100% - 50px);
            color:rgb(0, 0, 0);
            }

        img{
            height: 20px;
            width: 30px;
        }

        .vote{
            position: relative;
            width: 100px;
            margin: 0 auto;
            .stars{
                background-image: linear-gradient(yellow,yellow);
                background-size: var(--voto-medio) 100%;
                background-repeat: no-repeat;
                color: transparent;
                background-clip: text;
                -moz-background-clip: text;
                -webkit-background-clip: text;    
                background-color: var(--sfondo-scheda);
                width: 100%;
                
                .material-icons-two-tone {
                    font-size: 18px;
                    letter-spacing: -8px;
                }
        
                z-index: 1;        
            }
        }
    }   

    .lato-b{  
        position:absolute;
        width: $width-card;
        height: $height-card;
        border: 1px solid green;
        border-radius: 5px;
        top:0;
        background-color: red;
        background-image: url(/img/404.jpeg);
         background-size: cover;
        z-index:0;
        transform: rotateY(180deg);
        transition: transform 2s , z-index 2s;

        img{
            width: $width-card;
            height: $height-card;
        }
    }

    &:hover .lato-b{ 
        transform: rotateY(360deg);
        z-index:1;
    }
    
    &:hover .lato-a{ 
        z-index: 0;
        transform: rotateY(180deg);
    }
    
    
}


</style>

/*
esempio img https://image.tmdb.org/t/p/w500/u1z05trCA7AuSuDhi365grwdos1.jpg
 */