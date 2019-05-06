<template>
  <div class="outbox">
    <div class="inbox">
      <!--左侧内容-->
      <div class="inleftbox">
        <!-- addpart 开始 -->
        <div class="boxonedownaddoutbox">
          <div class="boxonedownaddoutbox_leftoutbox">
            <div class="boxonedownaddoutbox_leftoutbox_leftbox">
              <div class="boxonedownaddoutbox_leftoutbox_leftbox_textbox">
                <span>调度总次数：</span>
                <span>56次</span>
              </div>
            </div>
            <div class="boxonedownaddoutbox_leftoutbox_rightbox">返回当前</div>
          </div>
          <div class="boxonedownaddoutbox_rightoutbox">
            <div class="boxonedownaddoutbox_rightoutbox_contentbox">
              <div class="boxonedownaddoutbox_rightoutbox_contentbox_num">
                <div v-for="(item,index) in 24" :key="index" class="kdnum">{{item-1}}</div>
              </div>
              <div class="boxonedownaddoutbox_rightoutbox_contentbox_kedu">
                <div
                  v-for="(itemline,indexline) in 96"
                  :key="indexline"
                  :style="{width:1+'px'}"
                  :class="indexline%4==0?'longkd':'shortkd'"
                ></div>
              </div>
            </div>
            <!-- 需要定位的点击hover的刻度线开始 -->
            <div class="boxonedownaddoutbox_rightoutbox_contentbox_dwkeduline">
              <div
              ref="linep"
                v-for="(itemlinep,indexlinep) in ddstate"
                :key="indexlinep"
                class="linep"
                :class="itemlinep==1?'stateactive':''"
                :id="nowIndex==indexlinep?'clicactive':''"
                @click="selectlineactive(indexlinep)"
                :tooltip="timetip" placement="top"
              >
              <span id="tooltiptext" v-if="nowIndex==indexlinep">123</span>
              </div>
            </div>
      
            <!-- 需要定位的点击hover的刻度线结束 -->
          </div>
        </div>
        <!-- addpart 结束 -->
      </div>

      <!--右侧内容-->
      
    </div>
  </div>
</template>
<script>

export default {
  name: "Index",
  data() {
    return {
      /* dw刻度线模拟数据开始 */
      ddstate: [],
      nowIndex: 36,
      /* dw刻度线模拟数据结束 */
      timetip:"19:12:13",
    };
  },
  mounted() {
    /* dw刻度线模拟数据开始 */
    this.getstate();
    /* dw刻度线模拟数据结束 */
  /*   this.$nextTick(
        function(){
              var linep = document.getElementsByClassName("linep")[0]
      console.log(linep)
            var spanObj = document.createElement('span');
            spanObj.className='tooltiptext'
            spanObj.innerHTML="19:13:13"
            linep.appendChild(spanObj);
        }
    ) */
  },
  methods: {
    /* dw刻度线模拟数据开始 */
    getstate() {
      var state = [];
      for (var i = 0; i < 1440; i++) {
        if (i % 2 == 0) {
          state.push(0);
        } else {
          state.push(1);
        }
      }
      this.ddstate = state;
      console.log("%cstate", "font-size:16px;color:red", state);
    },
    /* dw刻度线模拟数据结束 */
    selectlineactive(tem) {
      this.nowIndex = tem;
    }
  }
};
</script>
<style lang="scss" scoped>
.outbox {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
  width: 100vw;
  /*   background-color: aqua; */
}
.inbox {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-items: center;
  width: -moz-calc(100% - 40px);
  width: -webkit-calc(100% - 40px);
  width: calc(100% - 40px);
  /*  background-color: rgb(22, 235, 93); */
}
.inleftbox {
  /*  width: 60%; */
  width: 1128px;
  /*  background-color: blueviolet; */
}
.inrightbox {
  width: 40%;
  /*  background-color: rgb(15, 81, 143);*/
}
//左侧样式
.boxone {
  width: 100%;
  height: 362px;
  /* background-color: #201717; */
}
/* addpart 开始 */
.boxonedownaddoutbox {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  width: 100%;
  height: 28px;
  border-left: 1px #e4e4ec solid;
  margin-left: -1px;
}
.boxonedownaddoutbox_leftoutbox {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-between;
  align-items: center;
  width: 216px;
  height: 28px;
  background-color: #273242;
}
.boxonedownaddoutbox_leftoutbox_leftbox {
  width: calc(100% - 56px);
  height: 28px;
  /* margin-left: 20px; */
  /* background-color: #e4e4ec */
}
.boxonedownaddoutbox_leftoutbox_leftbox_textbox {
  margin-left: 20px;
  font: normal 12px/28px "微软雅黑";
  color: #00ccff;
}
.boxonedownaddoutbox_leftoutbox_rightbox {
  width: 56px;
  height: 18px;
  border-radius: 2px;
  margin-right: 10px;
  font: normal 12px/18px "微软雅黑";
  text-align: center;
  color: #202833;
  background-color: #abe931;
}
.boxonedownaddoutbox_rightoutbox {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: flex-end;
  align-items: center;
  width: calc(100% - 216px);
  height: 28px;
  background-color: #111d30;
  position: relative;
}
/* 需要定位的点击hover的刻度线开始 */
.boxonedownaddoutbox_rightoutbox_contentbox_dwkeduline {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-between;
  align-items: flex-end;
  width: 763px;
  height: 27px;
  position: absolute;
  right: 37px;
  z-index: 22;
  /* background-color: blueviolet */
}
.linep {
  width: 1px;
  /* height: 27px; */
     position: relative;
        /* display: inline-block;
        border-bottom: 1px dotted black; */
        /* margin-top: 200px; */
}
.linep:hover {
  width: 1px;
  height: 27px;
  background-color: #abe931;
}
.stateactive {
  height: 27px;
  background-color: #5f8b09;
}
#clicactive {
  height: 27px;
  background-color: #00ccff;
}
/* 需要定位的点击hover的刻度线结束 */
.boxonedownaddoutbox_rightoutbox_contentbox {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
  width: 763px;
  height: 27px;
  margin-right: 37px;

  /*  background-color: #1f688a; */
}
.boxonedownaddoutbox_rightoutbox_contentbox_num {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-between;
  align-items: center;
  width: 763px;
  height: 14px;
  /*   background-color: blueviolet */
}
.kdnum {
  color: #5e6b7f;
  font: normal 12px "微软雅黑";
  margin-bottom: 2px;
}
.boxonedownaddoutbox_rightoutbox_contentbox_kedu {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-between;
  align-items: flex-end;
  width: 763px;

  /* background-color:#647185 */
}
.longkd {
  height: 6px;
  background-color: #647185;
}
.shortkd {
  height: 4px;
  background-color: #647185;
}

/* addpart 结束 */
.boxtwo {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-items: center;

  width: 100%;
  height: 48px;
  background-color: #fff;
}
.addoutbox {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-items: center;

  /*   margin: 0 20px; */

  width: 100%;
  /*   background-color: #70991f */
}

.boxthree {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: column;
  width: 100%;
  border-left: 1px #e4e4ec solid;
  border-bottom: 1px #e4e4ec solid;
  /*   background-color: #c5f35b; */
  overflow: auto;
}



/* 基本样式 */

/* tooltip样式 */
[tooltip] {
  position: relative;
}

[tooltip]::after {
  display: none;
  content: attr(tooltip);
  position: absolute;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  padding: 4px 8px;
  max-width: 200px;
  border-radius: 4px;
  box-shadow: 0 10px 20px -5px rgba(0, 0, 0, 0.4);
  z-index: 100;
}

[tooltip]::before {
  display: none;
  content: "";
  position: absolute;
  border: 5px solid transparent;
  border-bottom-width: 0;
  z-index: 100;
}

[tooltip]:hover::after {
  display: block;
}

[tooltip]:hover::before {
  display: block;
}

[tooltip][placement^="top"]::after,
[tooltip][placement^="top"]::before {
  animation: anime-top 300ms ease-out forwards;
}

/* 气泡主题 */
.tooltip-theme-dark,
[tooltip]::after {
  color: #6e7b8b;
  background-color: #111d30;
}

/* .tooltip-theme-light,
[tooltip][effect="light"]::after {
  color: #313131;
  background-color: #fff;
  border: 1px solid #313131;
} */

/* 气泡位置 */
/*----上----*/
.tooltip-placement-top,
[tooltip]:not([placement])::after,
[tooltip][placement=""]::after,
[tooltip][placement="top"]::after {
  bottom: calc(100% + 10px);
  left: 50%;
  transform: translate(-50%, 0);
}

/* 三角形主题 */
.triangle-theme-dark,
[tooltip]::before {
  border-top-color: #111d30;
}

/* .triangle-theme-light,
[tooltip][effect="light"]::before {
  border-top-color: #313131;
} */

/* 三角形位置 */
/*----上----*/
.triangle-placement-top,
[tooltip]:not([placement])::before,
[tooltip][placement=""]::before,
[tooltip][placement="top"]::before {
  bottom: calc(100% + 5px);
  left: 50%;
  transform: translate(-50%, 0);
}
/* @keyframes anime-top {
  from {
    opacity: 0.5;
    bottom: 150%;
  }
} */

/* 當前調度時刻 */
    #clicactive #tooltiptext {
        display:block;
        width: 60px;
        background-color: #00ccff;
        color: #202833;
        text-align: center;
        padding: 3px 0;
        position: absolute;
        z-index: 1;
        bottom: 130%;
        left: 50%;
        margin-left: -30px;
        font:normal 12px "微軟雅黑";
        z-index: 99;
        margin-bottom: 0px;
    }

    #clicactive #tooltiptext::after {
        content: "";
        position: absolute;
        top: 100%;
        left: 50%;
        margin-left: -5px;
        border-width: 5px;
        border-style: solid;
        border-color: #00ccff transparent transparent transparent;
    }
</style>

