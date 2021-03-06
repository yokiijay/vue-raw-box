<template>
  <div class="box" :class="{'box--avatar': avatar}" :style="{
    margin: selfCenter ? '0 auto' : '',
    flexDirection,
    flexWrap,
    justifyContent,
    alignItems,
    width,
    height,
    minWidth: width ? width : '',
    minHeight: height ? height : '',
    flex: flex ? parseFloat(flex) : ''
  }">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'Box',
  props: {
    left: Boolean,
    right: Boolean,
    top: Boolean,
    bottom: Boolean,
    center: Boolean,
    wrap: Boolean,
    row: Boolean,
    alignX: String,
    alignY: String,
    size: [String, Number, Array],
    selfCenter: Boolean,
    flex: [String, Number],
    avatar: Boolean
  },
  computed: {
    flexDirection(){
      return this.row ? 'row' : 'column'
    },
    flexWrap(){
      return this.wrap ? 'wrap' : 'nowrap'
    },
    justifyContent(){
      let justifyContent = 'flex-start'

      if(this.row){ //横着
        if(this.center) justifyContent = 'center'
        if(this.left) justifyContent = 'flex-start'
        if(this.right) justifyContent = 'flex-end'
        if(this.alignX) justifyContent = this.alignX
      }else {//竖着
        if(this.center) justifyContent = 'center'
        if(this.top) justifyContent = 'flex-start'
        if(this.bottom) justifyContent = 'flex-end'
        if(this.alignY) justifyContent = this.alignY
      }

      return justifyContent
    },
    alignItems(){
      let alignItems = 'flex-start'

      if(!this.row){ //竖着
        if(this.center) alignItems = 'center'
        if(this.left) alignItems = 'flex-start'
        if(this.right) alignItems = 'flex-end'
        if(this.alignX) alignItems = this.alignX
      }else {//横着
        if(this.center) alignItems = 'center'
        if(this.top) alignItems = 'flex-start'
        if(this.bottom) alignItems = 'flex-end'
        if(this.alignY) alignItems = this.alignY
      }

      return alignItems
    },
    width(){
      if(!this.size) return
      switch(this.size.constructor.name){
        case 'String':
          return this.size.match(/^\d+$/) ? this.size*1+'px' : parseFloat(this.size)+'px'
        case 'Number':
          return this.size
        case 'Array':
          if(!this.size[0]) return 'auto'
          return this.size[0].toString().match(/^\d+$/) ? this.size[0]*1+'px' : parseFloat(this.size[0])+'px'
        default:
          return false
      }
    },
    height(){
      if(!this.size) return
      switch(this.size.constructor.name){
        case 'String':
          return this.size.match(/^\d+$/) ? this.size*1+'px' : parseFloat(this.size)+'px'
        case 'Number':
          return this.size
        case 'Array':
          if(!this.size[1]) return 'auto'
          return this.size[1].toString().match(/^\d+$/) ? this.size[1]*1+'px' : parseFloat(this.size[1])+'px'
        default:
          return false
      }
    },
    objectFit(){
      switch(this.fit.constructor.name){
        case 'String':
          return this.fit
        case 'Boolean':
          return 'cover'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.box {
  display: flex;
}
.box--avatar {
  overflow: hidden;
  border-radius: 50%;

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
}
</style>
