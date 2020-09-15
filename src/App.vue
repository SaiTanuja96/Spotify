<template>
  <div class="bg-dark h-screen">

  <div class="flex" style="height: 88vh;">
  <!-- side nav -->
  <div class="w-56 bg-black h-full flex-none">
    <div class="p-6">
      <img src="./assets/images/spotifylogo.png" class="h-10">
    </div>
    <div class="mx-2 mb-5" v-for="page in pages" >
      <button @click="setID=page.id"  :class="`w-full focus:outline-none text-sm font-semibold rounded px-3 py-2 flex items-center justify-start ${setID=== page.id ? 'bg-light text-white' : 'text-light'}`">
      <font-awesome-icon style="color: white" :icon="page.icon" class="mr-3" />
<p style="color: white">{{page.name}}</p>
   </button>
    </div>
    <div class="mx-5">
      <h1 class=" mb-3 text-sm text-lightest tracking-widest uppercases">PLAYLISTS</h1>
    <button class="flex mb-5 items-center justify-start opacity-75 hover:opacity-100 mb-2">
      <img class="addnew" src="./assets/images/addnew.png">
      <p class="text-sm text-white font-semibold">Create Playlist</p>
    </button>
     <button class="flex mb-5 items-center justify-start opacity-75 hover:opacity-100 mb-2">
      <img class="addnew" src="./assets/images/heart.jpeg">
      <p class="text-sm text-white font-semibold">Liked Songs</p>
    </button>
    <div class="h-px w-full bg-light my-3">
    </div>
      </div>
      <div class="mx-5 mb-5">
        <div class="w-full h-10 overflow-y-scroll  mb-5 ">
          <p v-for="album in albums" class="text-lightest hover:text-white text-sm py-1">{{album.name}}</p>
        </div>
        <button class="flex py-2 items-center justify-start text-lightest hovertext-white">
     <img class="addnew mr-3  border-lightest" src="./assets/images/download.png">
      <p class="text-sm text-white font-semibold">Install App</p>
    </button>
      </div>
    <div class="relative pt-2">
     
      <div class="w-full h-full justify-end items-start opacity-0 hover:opacity-100 absolute">
     <div class="h-6 w-8 justify-end pt-2">
      <img src="./assets/images/downarrow.jpeg" class="downarrow">
      </div>
      </div>
      <img src="./assets/images/playpicture.jpeg" class="h-full">
    </div>
    </div>
    <!-- main content -->
<div class="w-full h-full relative overflow-y-scroll">
<!-- header -->
<div class="w-full sticky top-0 flex  py-4 px-6 bg-dark items-center justify-between">
<div class="flex items-center">
  <button class="bg-black w-8 h-8 text-white mr-3">
    <img src="./assets/images/lessthan.png">
  </button>
   <button class="bg-black w-8 h-8 text-white">
    <img src="./assets/images/greaterthan.png">
  </button>
</div>
<div class="relative">
  <button @click="showDropdown = true" class=" focus:outline-none bg-light rounded-full py-1 px-2 flex items-center">
  <img class="profilepic mr-2  h-6 w-6" src="./assets/images/profilepic.png">
  <p class="text-white font-semibold text-xs mr-3">Tanuja</p>
        <img src="./assets/images/scrolldown.png" class="h-4 w-4">

  </button>
  <div v-if="showDropdown === true" class="absolute  bg-light w-full round mt-1 items-center justify-center">
    <button @click="showDropdown = false" class="py-2 ml-8 text-sm  text-lightest hover:text-white border-b border-light">Account</button><br>
     <button @click="showDropdown = false" class="py-2 ml-8 text-sm text-lightest hover:text-white border-b border-light">LogOut</button>
 
  </div>
</div>
</div>
<!-- cards -->
<div px-6 py-3>
<div class="px-6 py-3 flex items-center justify-between">
  <h1 class=" pl-2 text-2xl font-semibold text-white tracking-wider hover:underline">Recently Played</h1>
<h2 class="text-xs pr-8 mb-3 text-lightest uppercase tracking-wider hover:underline">See All</h2>
</div>
<div class="w-full flex flex-wrap">
  <div v-for="recent in recents" class="p-2 w-55 relative justify-center itms-center ml-20">
    <div class="absolute w-full opacity-0 hover:opacity-100 h-full flex items-end justify-end p-8">
      <div class="bg-green rounded-full h-10 w-10 flex items-center justify-center">
<button>
  <img src="./assets/images/play.png">
</button>
    </div>
    </div>
    
    
    <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
      <img :src="`${recent.src}`" class="h-auto w-full shadow mb-2">
      <h1 class="text-sm font-semibold text-white tracking-wide">{{recent.title}}</h1>
      <h2 class="text-xs text-lightest tracking-wide">{{recent.artist}}</h2>
    </div>
</div>
</div>
</div>
<div px-6 py-3>
<div class="pl-2">
  <h1 class="text-2xl font-semibold text-white mb-2 tracking-wider hover:underline">Made for Tanuja</h1>
<h2 class="text-xs pr-8 mb-3 text-lightest">Get recommendations the more you listen</h2>
</div>
<div class="w-full flex flex-wrap">
  <div v-for="custom in customs" class="p-2 w-55 justify-center items-center ml-20 relative">
     <div class="absolute w-full opacity-0 hover:opacity-100 h-full flex items-end justify-end p-8">
      <div class="bg-green rounded-full h-10 w-10 flex items-center justify-center">
<button>
  <img src="./assets/images/play.png">
</button>
    </div>
    </div>

    <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
      <img :src="`${custom.src}`" class="h-auto w-full shadow mb-2">
      <h1 class="text-sm font-semibold text-white tracking-wide">{{custom.title}}</h1>
      <h2 class="text-xs text-lightest tracking-wide">{{custom.artist}}</h2>
    </div>
</div>
</div>
</div>

 
</div>
</div>

   <!-- playbar -->
   <div class="w-full bg-light flex items-center border-t border-dark justify-between px-3 bg-light" style="height: 12vh;">
 <div class="flex items-center">
   <div>
     <h1 class=" mb-1text-sm text-white tracking-white tracking-wide">Summer in the city-Remastered</h1>
     <h2 class="text-xs text-lightest tracking-wide">The Lovin' Spoonfull</h2>
   </div>
   <img class="h-6 w-6 mx-4" src="./assets/images/green-heart.png">
      <img class="h-6 w-6 mx-2" src="./assets/images/picinpic.png">

 </div>
 <div class="flex flex-col justify-center w-1/3 items-center">
   <div class="flex items-center">
     <button class="text-lg mr-5  bg-lightest  h-6 w-6 text-lightest hover:text-whtie">
       <img src="./assets/images/shuffle1.png">
     </button>
     <button   class="text-lg mr-5 bg-lightest h-6 w-6 text-lightest hover:text-whtie">
       <img  src="./assets/images/next.png">
     </button>
     <button   class="text-lg mr-5 h-10 w-10 text-lightest hover:text-whtie">
       <img @click.prevent="changesongState()" v-if="!songToggle" src="./assets/images/play.png">
       <img @click.prevent="changesongState()"  v-if="songToggle" src="./assets/images/pause.png">
     </button>
 
     <button class="text-lg mr-5 bg-lightest h-6 w-6 text-lightest hover:text-whtie">
       <img src="./assets/images/previous.png">
     </button>
     <button class="text-lg mr-5 bg-lightest h-6 w-6 text-lightest hover:text-whtie">
       <img src="./assets/images/repeat.png">
     </button>
   </div>
   <div class="w-full flex items-center mt-3">
     <p class="text-xs text-lightest mr-1">0:28
     </p>
   <div class="w-full h-1 bg-dark rounded-full  flex items-center">
     <div class="h-1 rounded-full bg-green" style="width:18%">
     </div>
     <div class="h-3 w-3 bg-white rounded-full -ml-1 shadow">
</div>
   </div>
    <p class="text-xs text-lightest ml-1">2:15
     </p>
   </div>
 </div>
 <div class="flex items-center">
   <img class="text-base bg-white text-lightest h-6 w-6" src="./assets/images/playlistplay.png">
  <img class="text-base bg-white text-lightest h-6 w-6 mx-3" src="./assets/images/important.png">
    <img class="text-base bg-white text-lightest h-6 w-6 mx-0" src="./assets/images/speaker.png">
<div class="w-20 ml-1 bg-lightest rounded-full h-1 ">
</div>
<div class="h-3 w-3 bg-white rounded-full -ml-1 shadow">
</div>

</div>
 
 
  </div>
  </div>
</template>
<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

export default {
  name: 'App',
  components:{
    FontAwesomeIcon
  },
  data: function() {
    return {
pages: [
  {id: 'home', name:'Home', icon:'home'},
  {id: 'search', name:'Search', icon:'search'},
  {id: 'library', name:'Your Library', icon:'book'}

],
setID:'home',
songToggle: false,
albums: [
  {name: 'drive'},
  {name: 'zhu'},
  {name: 'romantic'},
  {name: 'devotional'},
  {name: 'rock'},
  {name: 'slow'}
],
showDropdown:false,
recents: [
  {src: "album1.jpeg", title:'Mix 1', artist:'By Spotify'},
    {src: "album3.jpeg", title:'Mix 2', artist:'By Spotify'},
  {src: 'album1.jpeg', title:'Mix 3', artist:'By Spotify'},
  {src: 'album3.jpeg', title:'Mix 4', artist:'By Spotify'},
  {src: 'album1.jpeg', title:'Mix 5', artist:'By Spotify'},
  {src: 'album3.jpeg', title:'Mix 6', artist:'By Spotify'}

],
customs: [
  {src: "album1.jpeg", title:'Mix 1', artist:'By Spotify'},
    {src: "album3.jpeg", title:'Mix 2', artist:'By Spotify'},
  {src: 'album1.jpeg', title:'Mix 3', artist:'By Spotify'},
  {src: 'album3.jpeg', title:'Mix 4', artist:'By Spotify'},
  {src: 'album1.jpeg', title:'Mix 5', artist:'By Spotify'},
  {src: 'album3.jpeg', title:'Mix 6', artist:'By Spotify'}

],
pause:false,
audio : new Audio('song.mp3')
    };
  },
  methods: {
playSong(song){
  if(song){
    console.log("clicked")
    var audio = new Audio(song);
    audio.play();
    console.log(audio.played)
  }
},
 stopSong(song){
 if(song){
     console.log("unclicked")
     var audio = new Audio(song);
     audio.pause();
   }
 },

 changesongState(){
   
   if(!this.songToggle){
     this.audio.play()
     this.songToggle = !this.songToggle
   }else{
     this.audio.pause();
     this.songToggle = !this.songToggle
   }
 }

  }
}


</script>
<style>
.addnew{
  height: 25px;
  padding-right: 12px;
}
.downarrow{
  margin-left:185px;
}
.profilepic{
  /* height: 25px;
  border-radius: 2rem; */
}

</style>
