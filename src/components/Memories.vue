<template>
<div class="mem-container">
<div class="bgcolor">
    <full-page :options="options" style="z-index:100;">
      <!--第一屏-->
      <div class="section">
        <div class="ly-box01" :class="{anim: show}">
          <div class="ly-txt01">
            <p class="ly-stxt01" :class="{anim1: show}">摊位上一朵艳阳</p>
            <p class="ly-stxt02" :class="{anim2: show}">摊位上一朵艳阳</p>
            <p class="ly-stxt03" :class="{anim3: show}">摊位上一朵艳阳</p>
            <p class="ly-stxt04" :class="{anim4: show}">摊位上一朵艳阳</p>
            <p class="ly-stxt05" :class="{anim5: show}">摊位上一朵艳阳</p>
            <p class="ly-stxt06" :class="{anim6: show}">摊位上一朵艳阳</p>
            <p class="ly-stxt07" :class="{anim7: show}">祝：最亲爱的生日快乐！</p>
            <img v-if="firstImg" class="anim8" style="width: 50%; border-radius: 4px" :src="require('../assets/img/22.jpg')" alt="">
          </div>
        </div>
      </div>

      <!--第二屏-->
      <div class="section">
        <div class="timeline"></div>
        <div class="timepoint11"></div>
        <div class="ly-box11">
          <div class="ly-txt11">
              2021-11-11
          </div>
          <div class="ly-txt12">
            <p>摊位上一朵艳阳</p>
            <p>摊位上一朵艳阳</p>
            <p>摊位上一朵艳阳</p>
            <img class="time-img" style="width: 60%; margin-left: 0" :src="require('../assets/img/22.jpg')" alt="">
            <p>跟玫瑰很配哦</p>
          </div>
        </div>
        <div class="ly-triangle11"></div>
      </div>

      <!--第三屏-->
      <div class="section" v-for="i of 5">
        <div class="timeline"></div>
          <div class="timepoint21"></div>
          <div class="ly-box21">
            <div class="ly-txt21">
              2022-01-26
            </div>
            <div class="ly-txt22">
              <p>摊位上一朵艳阳</p>
              <p>摊位上一朵艳阳</p>
              <p>摊位上一朵艳阳</p>
              <img class="time-img" style="width: 60%" :src="require('../assets/img/22.jpg')" alt="">
              <p>很乖巧</p>
              <br>
              <br>
              <div @click.passive="fireShow = true" style="padding: 5px; border-radius: 4px; border: 1px solid #fff; text-align: center">打开烟花！</div>
            </div>
          </div>
          <div class="ly-triangle21"></div>
      </div>

      </full-page>

  <!--试验-->
  <ul class="bg-bubbles">
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
  </ul>

</div>
  <Fire v-if="fireShow" />
</div>
</template>

<script>
import Fire from './fire.vue'

let timer = null
export default {
  components: {
    Fire
  },
  data () {
    return {
      fireShow: false,
      show: false,
      firstImg: false,
      options: {
        navigation: true,
        navigationPosition: 'left',
        licenseKey: 'OPEN-SOURCE-GPLV3-LICENSE',
        sectionSelector: '.section',
        afterLoad: this.afterLoad
      }
    }
  },
  methods: {
    afterLoad (origin, destination, direction) {
      console.log('After load....')
      console.log(destination)
      if (+destination.index === 0) {
        this.show = true
        clearTimeout(timer)
        timer = setTimeout(() => {
          this.firstImg = true
        }, 12000)
      } else this.show = this.firstImg = false
    }
  }
}
</script>

<style lang="less">
.mem-container {
  height: 100%;
  width: 100%;

  .bgcolor {
    background: #ee9ca7;
    background: -webkit-linear-gradient(top left, #ee9ca7 0%, #ee9ca7 100%);
    background: linear-gradient(to bottom right, #ee9ca7 0%, #ee9ca7 100%);
    opacity: 0.9;
  }
  .bg-bubbles {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
  }
  .bg-bubbles li {
    position: absolute;
    list-style: none;
    display: block;
    width: 40px;
    height: 40px;
    background-color: rgba(255, 255, 255, 0.15);
    bottom: -160px;
    -webkit-animation: square 30s infinite;
    animation: square 30s infinite;
    -webkit-transition-timing-function: linear;
    transition-timing-function: linear;
  }
  .bg-bubbles li:nth-child(1) {
    left: 10%;
  }
  .bg-bubbles li:nth-child(2) {
    left: 20%;
    width: 80px;
    height: 80px;
    -webkit-animation-delay: 2s;
            animation-delay: 2s;
    -webkit-animation-duration: 17s;
            animation-duration: 17s;
  }
  .bg-bubbles li:nth-child(3) {
    left: 25%;
    -webkit-animation-delay: 4s;
            animation-delay: 4s;
  }
  .bg-bubbles li:nth-child(4) {
    left: 40%;
    width: 60px;
    height: 60px;
    -webkit-animation-duration: 22s;
            animation-duration: 22s;
    background-color: rgba(255, 255, 255, 0.25);
  }
  .bg-bubbles li:nth-child(5) {
    left: 70%;
  }
  .bg-bubbles li:nth-child(6) {
    left: 80%;
    width: 120px;
    height: 120px;
    -webkit-animation-delay: 3s;
            animation-delay: 3s;
    background-color: rgba(255, 255, 255, 0.2);
  }
  .bg-bubbles li:nth-child(7) {
    left: 32%;
    width: 160px;
    height: 160px;
    -webkit-animation-delay: 7s;
            animation-delay: 7s;
  }
  .bg-bubbles li:nth-child(8) {
    left: 55%;
    width: 20px;
    height: 20px;
    -webkit-animation-delay: 15s;
            animation-delay: 15s;
    -webkit-animation-duration: 40s;
            animation-duration: 40s;
  }
  .bg-bubbles li:nth-child(9) {
    left: 25%;
    width: 10px;
    height: 10px;
    -webkit-animation-delay: 2s;
            animation-delay: 2s;
    -webkit-animation-duration: 40s;
            animation-duration: 40s;
    background-color: rgba(255, 255, 255, 0.3);
  }
  .bg-bubbles li:nth-child(10) {
    left: 90%;
    width: 160px;
    height: 160px;
    -webkit-animation-delay: 11s;
            animation-delay: 11s;
  }
  /***                                  内容区域                                 ***/
  /**                                   第一部分                                  **/
  /*盒子*/
  .ly-box01 {
    width:50px;
    height:50px;
    background-color:#FFF;
    border-radius: 25px;
    position: absolute;
    left: 48%;
    bottom: 80%;
    margin-bottom:50%;
    overflow: hidden;
    transform-origin:center bottom;
  }
  .anim {
    animation:box_to_point 18.5s 0s,bounce 2.5s 18.5s;
  }

  /*文本*/
  .ly-txt01 {
    position:absolute;
    width: 100%;
    left: 0.5rem;
    top: 1rem;
    font-size: 20px;
  }
  .ly-stxt01 {
    font-family: Microsoft YaHei;
    position: relative;
    left: 1%;
    top: 5%;
    opacity: 0;

  }
  .anim1 {
    animation:ly-stxt01_move 15s;
    animation-delay:3s;
    -webkit-animation:ly-stxt01_move 15s;
    -webkit-animation-delay:3s;
  }

  .ly-stxt02 {
    font-family: Microsoft YaHei;
    position: relative;
    left: 1%;
    top: 5%;
    margin-top:-71px;
    opacity: 0;

  }

  .anim2 {
    animation:ly-stxt02_move 15s;
    animation-delay:3s;
    -webkit-animation:ly-stxt02_move 15s;
    -webkit-animation-delay:3s;
  }

  .ly-stxt03 {
    font-family: Microsoft YaHei;
    position: relative;
    left: 1%;
    top: 5%;
    opacity: 0;
    margin-top:-71px;

  }

  .anim3 {
    animation:ly-stxt03_move 15s;
    animation-delay:3s;
    -webkit-animation:ly-stxt03_move 15s;
    -webkit-animation-delay:3s;
  }

  .ly-stxt04 {
    font-family: Microsoft YaHei;
    position: relative;
    left: 1%;
    top: 5%;
    opacity: 0;
    margin-top:-71px;

  }

  .anim4 {
    animation:ly-stxt04_move 15s;
    animation-delay:3s;
    -webkit-animation:ly-stxt04_move 15s;
    -webkit-animation-delay:3s;
  }
  .time-img {
    margin-left: 1rem;
    border-radius: 4px;
  }

  .ly-stxt05 {
    font-family: Microsoft YaHei;
    position: relative;
    left: 1%;
    top: 5%;
    opacity: 0;
    margin-top:-71px;

  }

  .anim5 {
    animation:ly-stxt05_move 15s;
    animation-delay:3s;
    -webkit-animation:ly-stxt05_move 15s;
    -webkit-animation-delay:3s;
  }

  .ly-stxt06 {
    font-family: Microsoft YaHei;
    position: relative;
    left: 1%;
    top: 5%;
    opacity: 0;
    margin-top:-71px;

  }

  .anim6 {
    animation:ly-stxt06_move 15s;
    animation-delay:3s;
    -webkit-animation:ly-stxt06_move 15s;
    -webkit-animation-delay:3s;
  }

  .ly-stxt07 {
    font-family: Microsoft YaHei;
    position: relative;
    left: 1%;
    top: 5%;
    opacity: 0;
    margin-top:-71px;

  }

  .anim7 {
    animation:ly-stxt07_move 15s;
    animation-delay:3s;
    -webkit-animation:ly-stxt07_move 15s;
    -webkit-animation-delay:3s;
  }

  .anim8 {
    animation: anim8_move linear 6s forwards;
  }
  @keyframes anim8_move{
    0% {opacity:0;margin-top:-71px;}
    15% {opacity:1;margin-top:0;}
    50% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }


  /**                                      第二部分                                       **/
  /*时间轴的线*/

  .timeline {
    width: 8px;
    height: 0;
    position: absolute;
    left: 14%;
    top:-100%;
    background-color: #ccc;
    border-radius:3px;
    transition: all 2s;
  }
  .active .timeline {
    width: 10px;
    height: 100%;
    top:0;
    transition-delay: 0.1s;
  }
  /*时间轴上的点*/
  .timepoint {
    width: 20px;
    height: 20px;
    margin-left: -5px;
    position: absolute;
    left:20%;
    top: 15.5%;
    opacity: 0;
    background-color: #fff;
    -webkit-border-radius: 10px;
    -moz-border-radius: 10px;
    -ms-border-radius: 10px;
    -o-border-radius: 10px;
    border-radius: 10px;
    transition: all 0.3s;
  }
  .active .timepoint {
    opacity: 1;
    transition-delay: 2s;
  }
  /**时间轴上的点**/
  .timepoint11 {
    width: 20px;
    height: 20px;
    margin-left: -5px;
    position: absolute;
    left:14%;
    top: 0;
    opacity: 1;
    background-color: #fff;
    -webkit-border-radius: 10px;
    -moz-border-radius: 10px;
    -ms-border-radius: 10px;
    -o-border-radius: 10px;
    border-radius: 10px;
    transition: all 1s;
  }
  .active .timepoint11 {
    top:15.5%;
    transition-delay: 2s;
  }

  /* 盒子 */
  .ly-box11 {
    width: 70%;
    height: 600px;
    border: 2px #CCC;
    background-color: #fff;
    background-color: rgba(255,255,255,0.6);
    border-radius: 8px;
    position: absolute;
    left: 23%;
    top:10%;
    overflow: hidden;
    opacity: 0;
    -webkit-transform: scale(0.5, 0.5);
    transform: scale(0.5, 0.5);
    transition: all 1s;
  }
  .active .ly-box11{
    opacity: 0.9;
    -webkit-transform: scale(1, 1);
    transform: scale(1, 1);
    transition-delay: 2.5s;
  }
  /*小三角*/
  .ly-triangle11 {
    width: 0;
    height: 0;
    border-top: 20px solid transparent;
    border-right: 22px solid white;
    border-bottom: 20px solid transparent;
    border-radius: 2px;
    margin-left: 24px;
    position: absolute;
    right: 77%;
    top: 14%;
    opacity: 0;
    -webkit-transform: scale(0.5, 0.5);
    transform: scale(0.5, 0.5);
    transition: all 0.5s;
  }
  .active .ly-triangle11 {
    opacity: 0.6;
    margin-left: 2px;
    -webkit-transform: scale(1, 1);
    transform: scale(1, 1);
    transition-delay: 3.5s;
  }

  /*文本*/
  .ly-txt11 {
    font-family: Microsoft YaHei;
    font-size: 30px;
    text-shadow: 1px;
    position: absolute;
    left: 3%;
    top: 4%;
    opacity: 0;
    transition: all 0.5s;
  }

  .active .ly-txt11 {
    opacity: 1;
    transition-delay: 3.5s;
  }


  .ly-txt12 {
    font-family: Microsoft YaHei;
    font-size: 16px;
    position: absolute;
    padding-top: 20px;
    padding-left: 10px;
    left: 5%;
    top: 12%;
    opacity: 0;
    transition: all 1s;
  }

  .active .ly-txt12 {
    opacity: 1;
    transition-delay: 4s;
  }


  /**                                        第三部分                                  **/

  /**时间轴上的点**/
  .timepoint21 {
    width: 20px;
    height: 20px;
    margin-left: -5px;
    position: absolute;
    left:14%;
    top: 0;
    opacity: 1;
    background-color: #fff;
    -webkit-border-radius: 10px;
    -moz-border-radius: 10px;
    -ms-border-radius: 10px;
    -o-border-radius: 10px;
    border-radius: 10px;
    transition: all 0.5s;
  }
  .active .timepoint21 {
    top:15.5%;
    transition-delay: 1.5s;
  }

  /* 盒子 */
  .ly-box21 {
    width: 70%;
    height: 600px;
    border: 2px #CCC;
    background-color: #fff;
    background-color: rgba(255,255,255,0.6);
    border-radius: 8px;
    position: absolute;
    left: 23%;
    top:10%;
    overflow: hidden;
    opacity: 0;
    -webkit-transform: scale(0.5, 0.5);
    transform: scale(0.5, 0.5);
    transition: all 1s;
  }
  .active .ly-box21{
    opacity: 0.9;
    -webkit-transform: scale(1, 1);
    transform: scale(1, 1);
    transition-delay: 2.5s;
  }
  /*小三角*/
  .ly-triangle21 {
    width: 0;
    height: 0;
    border-top: 20px solid transparent;
    border-right: 22px solid white;
    border-bottom: 20px solid transparent;
    border-radius: 2px;
    margin-left: 24px;
    position: absolute;
    right: 77%;
    top: 14%;
    opacity: 0;
    -webkit-transform: scale(0.5, 0.5);
    transform: scale(0.5, 0.5);
    transition: all 0.5s;
  }
  .active .ly-triangle21 {
    opacity: 0.6;
    margin-left: 2px;
    -webkit-transform: scale(1, 1);
    transform: scale(1, 1);
    transition-delay: 3.5s;
  }

  /*文本*/
  .ly-txt21 {
    font-family: Microsoft YaHei;
    font-size: 30px;
    text-shadow: 1px;
    font-color: #000;
    position: absolute;
    left: 3%;
    top: 2%;
    opacity: 0;
    transition: all 0.5s;
  }

  .active .ly-txt21 {
    opacity: 1;
    transition-delay: 3.5s;
  }


  .ly-txt22 {
    font-family: Microsoft YaHei;
    font-size: 16px;
    text-indent: 1em;
    position: absolute;
    left: 5%;
    top: 8%;
    opacity: 0;
    transition: all 1s;
  }

  .active .ly-txt22 {
    opacity: 1;
    transition-delay: 4s;
  }

}
@-webkit-keyframes square {
  0% {
    -webkit-transform: translateY(0);
            transform: translateY(0);
  }
  100% {
    -webkit-transform: translateY(-900px) rotate(600deg);
            transform: translateY(-900px) rotate(600deg);
  }
}
@keyframes square {
  0% {
    -webkit-transform: translateY(0);
            transform: translateY(0);
  }
  100% {
    -webkit-transform: translateY(-900px) rotate(600deg);
            transform: translateY(-900px) rotate(600deg);
  }
}

  @keyframes bounce{
    0% {
      margin-bottom:0;
      width: 50px;
      height: 50px;
      border-radius: 25px;
      bottom:50%;
      left: 48%;
    }
    50% {
      margin-bottom:0;
      left: 48%;
      width: 50px;
      height: 50px;
      border-radius: 25px;
      bottom:0;
      left: 48%;
    }
    100% {
      margin-bottom:0;
      width: 20px;
      height: 20px;
      border-radius: 10px;
      left: 48%;
      bottom: 0;
      left: 20%;
    }
  }
  @-webkit-keyframes bounce{
      0% {
      margin-bottom:0;
      width: 50px;
      height: 50px;
      border-radius: 25px;
      bottom:50%;
      left: 48%;
    }
    50% {
      margin-bottom:0;
      left: 48%;
      width: 50px;
      height: 50px;
      border-radius: 25px;
      bottom:0;
      left: 48%;
    }
    100% {
      margin-bottom:0;
      width: 20px;
      height: 20px;
      border-radius: 10px;
      left: 48%;
      bottom: 0;
      left: 20%;
    }
  }
  @keyframes box_to_point{
    0% {
      margin-bottom:50%;
      width:50px;
      height:50px;
      border-radius: 25px;
      position: absolute;
      left: 48%;
      bottom: 20%;
      }
    10% {
      margin-bottom:0;
      width:50px;
      height:50px;
      border-radius: 25px;
      background-color:rgba(255,255,255,1);
      position: absolute;
      left: 48%;
      bottom: 20%;
    }
    14% {
      margin-bottom:0;
      width: 80%;
      height: 600px;
      border-radius: 6px;
      background-color:rgba(255,255,255,0.5);
      position: absolute;
      left: 10%;
      bottom: 5%;
    }
    96% {
      margin-bottom:0;
      width: 80%;
      height: 600px;
      border-radius: 6px;
      background-color:rgba(255,255,255,0.6);
      position: absolute;
      left: 10%;
      bottom: 5%;
    }
    100% {
      margin-bottom:0;
      width:50px;
      height:50px;
      border-radius: 25px;
      background-color:rgba(255,255,255,1);
      position: absolute;
      left: 48%;
      bottom: 50%;
    }
  }
  @-webkit-keyframes box_to_point{
    0% {
      margin-bottom:50%;
      width:50px;
      height:50px;
      border-radius: 25px;
      position: absolute;
      left: 48%;
      bottom: 50%;
      }
    10% {
      margin-bottom:0;
      width:50px;
      height:50px;
      border-radius: 25px;
      background-color:rgba(255,255,255,1);
      position: absolute;
      left: 48%;
      bottom: 50%;
    }
    14% {
      margin-bottom:0;
      width: 80%;
      height: 550px;
      border-radius: 6px;
      background-color:rgba(255,255,255,0.5);
      position: absolute;
      left: 10%;
      bottom: 12%;
    }
    96% {
      margin-bottom:0;
      width: 80%;
      height: 550px;
      border-radius: 6px;
      background-color:rgba(255,255,255,0.6);
      position: absolute;
      left: 10%;
      bottom: 12%;
    }
    100% {
      margin-bottom:0;
      width:50px;
      height:50px;
      border-radius: 25px;
      background-color:rgba(255,255,255,1);
      position: absolute;
      left: 48%;
      bottom: 50%;
    }
  }
  @keyframes ly-stxt01_move{
    0% {opacity:0;}
    8% {opacity:1;}
    90% {opacity:1;}
    98% {opacity:0;}
    100% {opacity:0;}
  }
  @-webkit-keyframes ly-stxt01_move{
    0% {opacity:0;}
    8% {opacity:0;}
    90% {opacity:1;}
    98% {opacity:0;}
    100% {opacity:0;}
  }
  @keyframes ly-stxt02_move{
    0% {opacity:0;margin-top:-71px;}
    8% {opacity:0;margin-top:-71px;}
    16% {opacity:1;margin-top:0;}
    90% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }
  @-webkit-keyframes ly-stxt02_move{
    0% {opacity:0;margin-top:-71px;}
    8% {opacity:0;margin-top:-71px;}
    16% {opacity:1;margin-top:0;}
    90% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }
  @keyframes ly-stxt03_move{
    0% {opacity:0;margin-top:-71px;}
    16% {opacity:0;margin-top:-71px;}
    24% {opacity:1;margin-top:0;}
    90% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }
  @-webkit-keyframes ly-stxt03_move{
    0% {opacity:0;margin-top:-71px;}
    16% {opacity:0;margin-top:-71px;}
    24% {opacity:1;margin-top:0;}
    90% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }
  @keyframes ly-stxt04_move{
    0% {opacity:0;margin-top:-71px;}
    24% {opacity:0;margin-top:-71px;}
    32% {opacity:1;margin-top:0;}
    90% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }
  @-webkit-keyframes ly-stxt04_move{
    0% {opacity:0;margin-top:-71px;}
    24% {opacity:0;margin-top:-71px;}
    32% {opacity:1;margin-top:0;}
    90% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }
  @keyframes ly-stxt05_move{
    0% {opacity:0;margin-top:-71px;}
    32% {opacity:0;margin-top:-71px;}
    40% {opacity:1;margin-top:0;}
    90% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }
  @-webkit-keyframes ly-stxt05_move{
    0% {opacity:0;margin-top:-71px;}
    32% {opacity:0;margin-top:-71px;}
    40% {opacity:1;margin-top:0;}
    90% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }
    @keyframes ly-stxt06_move{
    0% {opacity:0;margin-top:-71px;}
    40% {opacity:0;margin-top:-71px;}
    48% {opacity:1;margin-top:0;}
    90% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }
  @-webkit-keyframes ly-stxt06_move{
    0% {opacity:0;margin-top:-71px;}
    40% {opacity:0;margin-top:-71px;}
    48% {opacity:1;margin-top:0;}
    90% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }
      @keyframes ly-stxt07_move{
    0% {opacity:0;margin-top:-71px;}
    48% {opacity:0;margin-top:-71px;}
    56% {opacity:1;margin-top:0;}
    90% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }
  @-webkit-keyframes ly-stxt07_move{
    0% {opacity:0;margin-top:-71px;}
    48% {opacity:0;margin-top:-71px;}
    56% {opacity:1;margin-top:0;}
    90% {opacity:1;margin-top:0;}
    100% {opacity:0;margin-top:0;}
  }

</style>
