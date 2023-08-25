<script setup>
 import { ref, computed } from 'vue'
 
 const random = ['ค้อน', 'กระดาษ', 'กรรไกร', 'ความรัก'];
 const playerRandom = ref("ค้อน"); // กำหนดค่าเริ่มต้นให้ playerRandom เป็น 'ค้อน'
 const botRandom = ref("กระดาษ"); // กำหนดค่าเริ่มต้นให้ botRandom เป็น 'กระดาษ'
 const losses = ref(0);
 const wins = ref(0);
 const draws = ref(0);


 function play(){
  botRandom.value = random[Math.floor(Math.random() * random.length)];
  playerRandom.value = random[Math.floor(Math.random() * random.length)];

  if (
    (botRandom.value === 'ค้อน' && playerRandom.value === 'กรรไกร') ||
    (botRandom.value === 'กระดาษ' && playerRandom.value === 'ค้อน') ||
    (botRandom.value === 'กรรไกร' && playerRandom.value === 'กระดาษ') ||
    (botRandom.value === 'ความรัก' && playerRandom.value === 'กรรไกร') ||
    (botRandom.value === 'ความรัก' && playerRandom.value === 'ค้อน') ||
    (botRandom.value === 'ความรัก' && playerRandom.value === 'กระดาษ')
  ) {
    losses.value++;
  } else if (
    botRandom.value === playerRandom.value
  ) {
    draws.value++;
  } else {
    wins.value++;
  }
}
 
function resetValues(){
   botRandom.value = "";
   playerRandom.value = "";
   losses.value = 0;
   wins.value = 0;
   draws.value = 0;
 };

 
 function RanImg(pic) {
  const romImgs = {
    'ค้อน':    "https://i.pinimg.com/564x/45/29/24/452924c5795faa76f9c32ac06dc58ba8.jpg",
    'กระดาษ': "https://i.pinimg.com/564x/c5/1e/ef/c51eefd6458889941fff518c31e924b4.jpg",
    'กรรไกร': "https://i.pinimg.com/564x/3b/de/9a/3bde9ab3b761eed629e74c9efce9807d.jpg",
    'ความรัก' : "https://i.pinimg.com/564x/f1/a7/71/f1a771739dfab103e7cc073277232da1.jpg" ,
  };
  return romImgs[pic];
}

const winPercentage = computed(() => {
    const total = wins.value + draws.value + losses.value
    return total ? (wins.value / total) * 100 : 0
  })



 </script>
 
 <template>
  
  <div>
    <header class="container">
      <h1 class="">เป่า ยิ้ง ฉุบ </h1>
    </header>
    <p><h2> Let's fun together!! </h2></p>
    <div class="container">

      <div class="playerbox">
        <p style="color: rgb(136, 141, 254);"><b>Player</b></p>  <br>
        <img class="imgsize" :src="RanImg(playerRandom)"/><br>
        {{ playerRandom }} <br>
      </div>

      &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp;
      
      <h1 style="color: rgb(128, 246, 154);">VS</h1>

      &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp;

      <div class="botbox">
        <p style="color: rgb(250, 65, 65);"><b> Bot</b> </p> <br>
        <img class="imgsize" :src="RanImg(botRandom)"/><br>
        {{ botRandom }}   
      </div> 
      
        <br>
    </div>


    <div>
        <span class="font-bold">Wins : </span> {{ wins }}   |
        <span class="font-bold">Draws : </span> {{ draws }}  |
        <span class="font-bold">Losses :</span> {{ losses }} 
      </div>

      <div class="text-lg">
        Wins Rates : {{ Math.round(winPercentage) }}%
      </div>
      
      <br>

      <div class="button-container">
    <button @click="play" class="button-zoom">
                เป่ายิ๊งงงงงงงงงงงง ฉุบบบบ!
        </button>

        &nbsp;&nbsp;&nbsp;

        <button @click="resetValues" class="button1"> เริ่มใหม่ </button>

      </div>
</div>
</template>

<style scoped>
.imgsize{
 width: 300px;
 height: 300px;
 border-width: none;
 border-radius: 45px;
}

.container{
  display: flex;
}

.botbox{
} 

.playbox{

}

h1{
  font-size: 70px;
  margin: auto;
}


.start{
  background-color: greenyellow;
}

.restart{
  background-color: red;
}

.button {
padding: 15px 25px;
  font-size: 24px;
  text-align: center;
  cursor: pointer;
  outline: none;
  color: #fff;
  background-color: #fdbd30;
  border: none;
  border-radius: 15px;
  box-shadow: 0 9px #ab6f08;
}

.button:hover {background-color: #e99220}

.button:active {
  background-color: #d59d0e;
  box-shadow: 0 5px #666;
  transform: translateY(4px);
}

.button1 {
padding: 15px 25px;
  font-size: 24px;
  text-align: center;
  cursor: pointer;
  outline: none;
  color: #fff;
  background-color: #fb1717;
  border: none;
  border-radius: 15px;
  box-shadow: 0 9px #960606;
}

.button1:hover {background-color: #c22d2d}

.button1:active {
  background-color: #8e0f0f;
  box-shadow: 0 5px #666;
  transform: translateY(4px);
}

.font-bold{
  font-weight: bold;
}
.button-container {
  display: flex;
  justify-content: center; /* จัดกึ่งกลางตามแนวนอน */
  gap: 10px; /* ระยะห่างระหว่างปุ่ม */
}

.button-zoom {
  padding: 15px 25px;
  font-size: 24px;
  cursor: pointer;
  outline: none;
  color: #fff;
  background-color: #f4b93a;
  border: none;
  border-radius: 15px;
  box-shadow: 0 9px #ab6f08;
  transition: transform 0.3s ease;
}

.button-zoom:hover {
  transform: scale(1.05); /* เพิ่มขนาดเล็กน้อยเมื่อ Hover */
}

.button1 {
  padding: 15px 25px;
  font-size: 24px;
  cursor: pointer;
  text-align: center;
  outline: none;
  color: #fff;
  background-color: #fb1717;
  border: none;
  border-radius: 15px;
  box-shadow: 0 9px #960606;
  transition: transform 0.3s ease; /* เพิ่มการเปลี่ยนแปลงเมื่อ Hover */
}

.button1:hover {
  transform: scale(1.3); /* ขยายปุ่มเมื่อ Hover */

}
</style>