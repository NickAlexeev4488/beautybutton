<script setup>
import { onMounted, ref, onUpdated } from 'vue'

let seasonname = ref('summer')
let names = ref('')
let col = ''


onMounted(() => {
  let seasoncol = document.getElementById('seasoncol')
  let begun = document.getElementById('begun')
  let pos = ''
})


let movebegunok = (n) => {
  if (n === 1){
    pos = 'firstpos'
    names.value = 'summer'
    col = 'firstcol'
  }
  else if (n === 2){
    pos = 'secondpos'
    names.value = 'autumn'
    col = 'secondcol'
  }
  else if (n === 3){
    pos = 'thirdpos'
    names.value = 'winter'
    col = 'thirdcol'
  }
  else{
    pos = 'fourthpos'
    names.value = 'spring'
    col = 'fourthcol'
  }
  if (begun.classList.contains('firstpos') && n != 1){
    begun.classList.remove('firstpos')
    seasoncol.classList.remove('firstcol')
  }
  else if (begun.classList.contains('secondpos') && n != 2){
    begun.classList.remove('secondpos')
    seasoncol.classList.remove('secondcol')
  }
  else if (begun.classList.contains('thirdpos') && n != 3){
    begun.classList.remove('thirdpos')
    seasoncol.classList.remove('thirdcol')
  }
  else if (begun.classList.contains('fourthpos') && n != 4){
    begun.classList.remove('fourthpos')
    seasoncol.classList.remove('fourthcol')
  }
  begun.classList.add(pos)
  seasonname.value = names.value
  seasoncol.classList.add(col)
}

</script>

<template>

<div class="cont">
  <div id="seasoncol" class="seasonname firstcol">
    <h3 class="nameh3">
      {{seasonname}}
    </h3>
  </div>
  <div class="tempcont">
    <div class="template">
      <div id="begun" class="begunok"></div>
      <div @click="movebegunok(1)" class="butseasons summer"></div>
      <div @click="movebegunok(2)" class="butseasons autumn"></div>
      <div @click="movebegunok(3)" class="butseasons winter"></div>
      <div @click="movebegunok(4)" class="butseasons spring"></div>
    </div>
  </div>
</div>
</template>

<style>

.cont{
  width: 100%;
  height: 600px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.template{
  width: 275px;
  height: 50px;
  display: flex;
  justify-content: space-between;
  position: relative;
}
.tempcont{
  width: 305px;
  height: 64px;
  background-color: rgb(237, 237, 237);
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 100px;
}



.begunok{
  width: 50px;
  height: 50px;
  position: absolute;
  background-color: rgb(111, 111, 111);
  border-radius: 50%;
  opacity: 50%;
}
.firstpos{
  margin-left: 0;
  transition: 400ms;
}
.secondpos{
  margin-left: 75px;
  transition: 400ms;
}
.thirdpos{
  margin-left: 150px;
  transition: 400ms;
}
.fourthpos{
  margin-left: 225px;
  transition: 400ms;
}



.seasonname{
  width: 400px;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  margin-bottom: 50px;
}
.nameh3{
  color: aliceblue;
  padding: 0;
  margin: 0;
  font-size: 70px;
  font-family: 'Courier New', Courier, monospace;
}
.firstcol{
  background-color: rgb(243, 52, 52);
}
.secondcol{
  background-color: rgb(181, 62, 19);
}
.thirdcol{
  background-color: rgb(55, 200, 205);
}
.fourthcol{
  background-color: rgb(52, 243, 74);
}

.butseasons{
  background-color: rgb(159, 159, 159);
  width: 50px;
  height: 50px;
}
.summer{
  background: center / contain url(src/assets/summer.png);
}
.autumn{
  background: center / contain url(src/assets/autumn.png);
}
.winter{
  background: center / contain url(src/assets/winter.png);
}
.spring{
  background: center / contain url(src/assets/spring.png);
}

</style>
