<template>
<div id="Search"> 
    <input name="text" id="query" placeholder="cerca" type="text" v-model.trim="testo" @keyup.enter.prevent.stop="$emit('invio',testo)">
    <input type="submit" value="invia" @click.stop="$emit('invio',testo)">
</div>
  
</template>

<script>
export default {
    name:'Search',
    data(){
        return{
            testo:'star',
        }
    }

}
</script>

<style lang="scss" scoped>

#Search{
    input{
        outline: none;
        border-radius: 5px 0 0 5px ;
        &:focus{
            background-image: linear-gradient(to bottom, #019ff9aa, #83cffaaa);
        }
    }


    input[type=submit]{
        border-radius: 0 5px 5px 0;
    }
    display: flex;
    align-items: center;
    justify-content: space-between;
    

}
</style>