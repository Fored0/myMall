<template>
  <div class="tab-bar-item" @click="itemClick">
    <div>
      <div v-if="!isActive"><slot name="item-icon"></slot></div>
      <div v-else><slot name="item-icon-active"></slot></div>
      <div :style="activeStyle"><slot name="item-text"></slot></div>
    </div>
  </div>
</template>

<script>
export default {
  name:'TabBarItem',
  props:{
    path:String,
    activeColor:{
      type:String,
      default:'red'
    }
  },
  computed:{
    isActive(){
      return this.$route.path.indexOf(this.path) !== -1
    },
    activeStyle(){
      return this.isActive ? {color:this.activeColor} : {}
    }
  },
  data(){
    return{
      // isActive:false,
    }
  },
  methods:{
    itemClick(){
      this.$router.replace(this.path)
      // this.isActive=!this.isActive
    }
  }
}
</script>

<style scoped>
  .tab-bar-item{
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 13px;
  }
  .tab-bar-item img{
    width: 20px;
    height: 20px;
    margin-top: 3px;
    /* 去除图片底部默认像素 */
    vertical-align: middle; 
    margin-bottom: 2px;
  }

</style>