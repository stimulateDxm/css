<template>
  <div>
      <div class="w"  >
        <!-- 道路外层 -->
        <div class="lu-outer">
          <!-- 道路内层 -->

          <div class="lu-core">
            <!-- 音乐-->
            <div><audio   src="@/assets/images/live.mp3" ref="audioed" preload="auto" ></audio></div>
            <!-- 道路里面的图片 -->

            <img alt="" src="@/assets/images/z.png">
            <!-- 开始提示框-->
            <div ref="starts" class="start" @click="goli()" >开始</div>

          </div>

        </div>
        <div class="xiaorei">
          <!-- 小人图片底部 -->

          <div v-show="isbottom"
               ref="classbottom bottom"
               :class="{bottom2:isbottom1}"
               class="imgs-bottom"
               @webkitAnimationEnd="bottomend"
          >
            <div :class="{bottom1:isbottom1}" class="big-bottom" ref="bottom">
              <img alt="" src="@/assets/images/bottom5.png">
              <img alt="" src="@/assets/images/bottom4.png">
              <img alt="" src="@/assets/images/bottom3.png">
              <img alt="" src="@/assets/images/bottom2.png">
              <img alt="" src="@/assets/images/bottom1.png">
            </div>

          </div>
          <!-- 小人图片左部 -->
          <div v-show="isleft"
               class="imgs-left"
               @webkitAnimationEnd="leftend"
               ref="left"
          >
            <div class="big-left" ref="left">
              <img alt="" src="@/assets/images/left5.png">
              <img alt="" src="@/assets/images/left4.png">
              <img alt="" src="@/assets/images/left3.png">
              <img alt="" src="@/assets/images/left2.png">
              <img alt="" src="@/assets/images/left1.png">
            </div>
          </div>
          <!-- 小人图片上部 -->

          <div v-show="istop"
               class="imgs-top"
               @webkitAnimationEnd="topend"
               ref="top"
          >
            <div class="big-top"  ref="top">
              <img alt="" src="@/assets/images/top5.png">
              <img alt="" src="@/assets/images/top4.png">
              <img alt="" src="@/assets/images/top3.png">
              <img alt="" src="@/assets/images/top2.png">
              <img alt="" src="@/assets/images/top1.png">
            </div>
          </div>
          <!-- 小人图片右部 -->
          <div v-show="isright"
               class="imgs-right"
               @webkitAnimationEnd="rightend"
               ref="right"
          >
            <div class="big-right"  ref="right">
              <img alt="" src="@/assets/images/right5.png">
              <img alt="" src="@/assets/images/right4.png">
              <img alt="" src="@/assets/images/right3.png">
              <img alt="" src="@/assets/images/right2.png">
              <img alt="" src="@/assets/images/right1.png">
            </div>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'Animations',
  data() {
    return {
      //控制底部小人开始状态
      isbottom1: false,
      isbottom: true,
      isleft: false,
      istop: false,
      isright: false
    }
  },
  methods: {

    //动画结束事件下
    bottomend() {
      this.isbottom = false
      this.isleft = true

    },
    //动画结束事件左
    leftend() {
      this.isleft = false
      this.istop = true
    },
    //动画结束事件上
    topend() {
      this.istop = false
      this.isright = true
    },
    //动画结束事件右
    rightend() {
      this.isright = false
      this.isbottom1 = false
      this.isbottom = true
      this.$refs.starts.style.display="block"

    },
    //点击开始跑步
    goli() {
      //控制点击开始按钮隐藏
      this.$refs.starts.style.display="none"
      //控制动画开始移动
      this.isbottom1 = true
      //控制音乐
      this.$refs.audioed.play().catch((error)=>{
        console.log(error)
      })
      //自动播放
      this.$refs.audioed.autoplay=true
      //循环播放
      this.$refs.audioed.loop=true

    },

  },
  mounted() {


  },
}

</script>

<style lang="less" scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.goren {
  position: absolute;
  left: 0;
  top: 0;
  width: 80px;
  height: 80px;
}

//外层大小
@width: 650px;
//里层大小
@-hundred: @width - 180;

.froms(@x1:0px,@y1:0px) {
  transform: translateX(@x1) translateY(@y1);
}

//小人动画
.froms(@x1: 0px, @y1: 0px) {
  transform: translateX(@x1) translateY(@y1);
}

//小人动画
@keyframes gobottom {
  from {
    .froms()
  }
  to {
    .froms(-80px * 5, 0px)
  }
}

@keyframes gobottom1 {

  from {
    .froms(550px, 540px);
  }
  to {
    .froms(0px, 540px);

  }


}

@keyframes goleft1 {
  from {
    .froms()
  }
  to {
    .froms(0px, -80 * 5px)
  }
}

@keyframes goleft {
  from {
    .froms(0px, 540px)
  }
  to {
    .froms()
  }
}

@keyframes gotop1 {
  from {
    .froms();
  }
  to {
    .froms(400px, 0)
  }
}

@keyframes gotop {
  from {
    .froms();
  }
  to {
    .froms(550px, 0)
  }
}

@keyframes goright1 {
  from {
    .froms()
  }
  to {
    .froms(0, -400px);
  }
}

@keyframes goright {
  from {
    .froms(550px, 0)
  }
  to {
    .froms(550px, 540px);
  }
}

.w {
  position: relative;
  //外层
  .lu-outer {
    width: @width;
    height: @width;
    border: 1px solid orange;
    background-color: aquamarine;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50px;


    //内层
    .lu-core {
      width: @-hundred;
      height: @-hundred;
      //border: 1px solid orange;
      background-color: pink;
      border-radius: 70px;
      //城市图
      img {
        width: @-hundred;
        height: @-hundred;
        border-radius: 70px;
      }

      // 开始提示框

      .start {
        text-align: center;
        width: 100px;
        height: 20px;
        line-height: 20px;
        border-radius: 10px;
        background-color: deepskyblue;
        opacity: 0.7;
        margin: 0 auto;
        .froms(0px, -@-hundred / 2);
        //display: none;


      }


    }
  }

  //小人图片
  .xiaorei {
    //小人物底部
    .bottom2 {
      animation: gobottom1 5s linear forwards;
    }

    .imgs-bottom {
      .goren;
      //background-color: orange;
      overflow: hidden;
      .froms(550px, 540px);


      .big-bottom {
        display: flex;
        flex-direction: row;
        .froms(0px, 0px);

      }

      .bottom1 {
        animation: gobottom 1s steps(5) 5;
      }
    }


    //小人物左边
    .imgs-left {
      .goren;
      //background-color: orange;
      overflow: hidden;
      .froms(0px, 540px);
      animation: goleft 5s linear forwards;
      //-webkit-animation-delay:5s;

      .big-left {
        display: flex;
        flex-direction: column;
        .froms();
        animation: goleft1 1s steps(5) infinite;
      }
    }

    //小人物上边
    .imgs-top {
      .goren;
      //background-color: orange;
      overflow: hidden;
      .froms();
      animation: gotop 5s linear forwards;
      //-webkit-animation-delay:10s;

      .big-top {
        display: flex;
        flex-direction: row-reverse;
        .froms();
        animation: gotop1 1s steps(5) infinite;
      }
    }

    //小人物右边
    .imgs-right {
      .goren;
      //background-color: orange;
      overflow: hidden;
      .froms(550px, 0);
      animation: goright 5s linear forwards;
      //-webkit-animation-delay:15s;

      .big-right {
        display: flex;
        flex-direction: column-reverse;
        .froms();
        animation: goright1 1s steps(5) infinite;
      }
    }
  }

}

</style>