<template>
<div id="Search"> 
    <input name="text" id="query" placeholder="cerca" type="text" v-model="testo" @keyup.enter.prevent="$emit('invio',testo)">
    <input type="submit" value="invia" @click="$emit('invio',testo)">
</div>
  
</template>

<script>
export default {
    name:'Search',
    data(){
        return{
            testo:'',
        }
    }

}
</script>

<style>

</style>