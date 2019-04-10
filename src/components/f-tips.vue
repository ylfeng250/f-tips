<template>
  <div class="tip-box">
    <slot></slot>
    <div class="tip" :style="styleObject" :position="position" data-color="#056">{{tip}}</div>
  </div>
</template>

<style scoped>
.tip-box{
  display: inline-block;
  position: relative;
  border: 1px solid red;
}

.tip {
  font-size:16px;
  position: absolute;
  border-radius: 5px;
  background: black;
  color: #ffffff;
  height: 1.6em;
  line-height: 1.6em;
  padding: 0 0.4em;
  white-space: nowrap;
  opacity: 0;
}
.tip::before {
  content: "";
  border-width: 0.5em;
  border-style: solid; 
  position: absolute;
}
.tip-box:hover .tip{
  opacity: 1;
}
/* top */
.tip[position=top] {
  top: -2em; 
  left: 0;
}
.tip[position=top]::before {
  transform: translateY(1.5em) scale(1, 1.5);
  border-style: solid;
  /* border-color: black transparent transparent  transparent; */
}
/* bottom */
.tip[position=bottom] {
  /* margin-top: 0.5em; */
  bottom: -2em;
  left: 0;
}
.tip[position=bottom]::before {
  transform: translateY(-1.1em) scale(1, 1.5);
  border-color: transparent transparent black transparent;
}
/* left */
.tip[position=left] {
  height: auto;
  width: 1em;
  white-space:pre-wrap;
  word-wrap: break-word;
  top: 0; 
  left: -2.5em;
}
.tip[position=left]::before {
  transform: translateX(1.3em);
  border-color: transparent transparent transparent black;
}
/* right */
.tip[position=right] {
  height: auto;
  width: 1em;
  white-space:pre-wrap;
  word-wrap: break-word;
  top: 0; 
  right: -2.5em;
}
.tip[position=right]::before {
  transform: translateX(-1.3em) scale(1.5, 1);
  border-color: transparent black transparent transparent ;
}
</style>

<script>
export default {
  props:{
    tip:{
      type:String,
      default:'tips'
    },
    fontSize:{
      type:String,
      default:'16px'
    },
    position:{
      type: String,
      default: 'top',
      validator: function (value) {
        // 这个值必须匹配下列字符串中的一个
        return ['top', 'bottom', 'left', 'right'].indexOf(value) !== -1
      }
    },
    backgroundColor:{
      type: String,
      default: 'black'
    },
    fontColor:{
      type: String,
      default: '#fff'
    }
  },
  name: 'tips',
  computed:{
    styleObject() {
      return {
        fontSize:this.fontSize,
        background:this.backgroundColor,
        color:this.fontColor
      }
    }
  }
}
</script>
