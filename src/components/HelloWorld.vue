<template>
 <div>
   <div class="box">
   <div class="container" v-for="(item,index) in 1024" :key="index" :tooltip="timetip" placement="top" @click="selectlineactive(index)"
   :id="nowIndex==index?'clicactive':''"></div>
 </div>
 <div class="box2">
    <index/>
 </div>
 </div>
</template>

<script>
import index from '@/components/index'
export default {
  name: "HelloWorld",
  components:{
    index
  },
  data() {
    return {
      timetip:"19:12:13",
      nowIndex:3
    };
  },
  methods:{
       selectlineactive(tem) {
      this.nowIndex = tem;
    }
  }
};
</script>
<style scoped>
.box2{
    width: 100vw;
  height: 28px;
  margin-top: 60px;
}
.box{
  width: 100vw;
  height: 27px;
  margin-top: 200px;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content:space-between;
  align-items: center;
}
#clicactive {
  height: 27px;
  background-color: #00ccff;
}

/* 基本样式 */
.container {
  width: 1px;
  height: 27px;
  cursor: pointer;
  background-color: rgb(204, 10, 10);
  appearance: none;

}

.container:hover {
  background-color: #409eff;
}

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
  padding: 8px 15px;
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
  color: #fff;
  background-color: #313131;
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
  border-top-color: #313131;
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
</style>


