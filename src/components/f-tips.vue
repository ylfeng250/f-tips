<template>
  <div class="tip-box">
    <slot></slot>
    <div class="tip" :style="styleObject" :position="position">{{tip}}</div>
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
  font-size: 1em;
  border-width: 0.5em;
  border-style: solid; 
  position: absolute;
  /* 设置颜色 */
  border-color: transparent;
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
  transform: translateY(1.6em) scale(1, 1.5);
  border-style: solid;
  border-top-color: var(--arrow-color)
}
/* bottom */
.tip[position=bottom] {
  /* margin-top: 0.5em; */
  bottom: -2em;
  left: 0;
}
.tip[position=bottom]::before {
  transform: translateY(-1em) scale(1, 1.5);
  border-style: solid;
  border-bottom-color: var(--arrow-color)
}
/* left */
.tip[position=left] {
  height: auto;
  width: 1em;
  white-space:pre-wrap;
  word-wrap: break-word;
  top: 0; 
  left: -2.1em;
}
.tip[position=left]::before {
  white-space: nowrap;
  word-wrap: none;
  transform: translateX(1.2em) scale(1.5, 1);
  border-style: solid;
  border-left-color: var(--arrow-color)
}
/* right */
.tip[position=right] {
  height: auto;
  width: 1em;
  white-space:pre-wrap;
  word-wrap: break-word;
  top: 0; 
  right: -2.1em;
}
.tip[position=right]::before {
  white-space: nowrap;
  word-wrap: none;
  transform: translateX(-1.2em) scale(1.5, 1);
  border-style: solid;
  border-right-color: var(--arrow-color)
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
        color:this.fontColor,
        '--arrow-color':this.backgroundColor
      }
    }
  }
}
</script>
