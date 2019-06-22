<template>
    <ul class="list">
        <li class="item" v-for="item of letters" :key='item' @click="handleLetterClick" @touchstart.prevent='handleTouchStart' @touchmove='handleTouchMove' @touchend='handleTouchEnd' :ref='item'>{{item}}</li>
    </ul>
</template>

<script>
export default {
    name:'CityAlphabet',
    props:{
        cities:Object
    },
    data(){
        return{
            touchStatus:false
        }
    },
    computed:{
        letters(){
            const letters=[]
            for(let i in this.cities){
                letters.push(i)
            }
            return letters
        }
    },
    methods:{
        handleLetterClick(e){
            this.$emit('change',e.target.innerText)
        },
        handleTouchStart(){
            this.touchStatus=true
        },
        handleTouchMove(e){
            if (this.touchStatus) {
                const startY=this.$refs['A'][0].offsetTop
                const touchY=e.touches.clientY-79
                const index=Math.floor((touchY-startY)/20)
                if (index >=0 &&index<this.letters.length) {
                     this.$emit('change',this.letters[index])
                }
               
            }
        },
        handleTouchEnd(){
             this.touchStatus=false
        }
    }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.list
    position absolute
    top 1.58rem
    right 0
    bottom 0
    width .4rem
    display flex
    flex-direction column
    justify-content center
    .item
        text-align center
        line-height .4rem
        color $bgColor
</style>
