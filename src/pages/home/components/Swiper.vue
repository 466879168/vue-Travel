<template>
<div class="wrapper">
    <swiper :options="swiperOption" v-if="showSwiper">
    <swiper-slide v-for="item of list" :key='item.id'>
        <img class="swiper-img" :src="item.imgUrl" alt="">
    </swiper-slide>
    <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
    name:'HomeSwiper',
    props:{
        list:Array
    },
    data(){
        return {
            swiperOption:{
                pagination:'.swiper-pagination',
                loop:true,
                autoplay:3000,
                //paginationClickable: true,
                //observer:true,//修改swiper自己或子元素时，自动初始化swiper
                //observeParents:true,//修改swiper的父元素时，自动初始化swiper
            }
        }
    },computed:{
        showSwiper(){
            return this.list.length
        }
    }
}
</script>

<style lang="stylus" scoped>
.wrapper >>> .swiper-pagination-bullet-active
    background #fff
.wrapper
    width 100%
    height 0
    overflow hidden
    padding-bottom 31.21%
    background-color #ccc
    .swiper-img
        width 100%  
</style>
