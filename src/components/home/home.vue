<template>
    <div class="page">
        <Header></Header>
        <div class="content">
            <Nav :navData='navData'></Nav>
            <div class="index-content">
               <div class="banner">
                    <mt-swipe  :auto="4000" :show-indicators="false" @change="handleChange">
                        <mt-swipe-item v-for="(item,index) in bannerData ">
                            <img :src="item.imgSrc" alt="">
                        </mt-swipe-item>
                    </mt-swipe>
                    <ul class="my-indicators">
                        <li v-for="(item,index) in bannerData"  :class="[index== swiperIndex?'indicator-active':'']" @click="handleChange(index)">
                            {{item.title}}
                        </li>   
                    </ul>
               </div>
               <div v-infinite-scroll="loadMore" 
                infinite-scroll-disabled="loading"
                infinite-scroll-distance="10">
                    <ContentItem v-for="(item,index) in ContentItemData" :data='item'></ContentItem>
               </div>
            </div>
        </div>
    </div>
</template>

<script type="text/ecmascript-6">
import Header from '../header/header'
import Nav from '../nav/nav'
import ContentItem from '../indexContentItem/ContentItem'
import Vue from 'vue'
import { Swipe, SwipeItem } from 'mint-ui'
Vue.component(Swipe.name, Swipe);
Vue.component(SwipeItem.name, SwipeItem);
export default {
    name: 'Home',
    data() {
        return {
            navData: {},
            bannerData:{},
            swiperIndex:0,
            ContentItemData:{}
        }
    },
    components: {
        Header,
        Nav,
        ContentItem
    },
    mounted() {
        
    },
    created() {
        this.getData();
    },
    methods: {
        getData:function(){
            const url = 'https://www.easy-mock.com/mock/5b1753d3cbe2f85929997f52/api/toutiaoNavData';
            this.$ajax.get(url).then(res=>{
                this.navData = res.data.data,
                this.bannerData = res.data.bannerData,
                this.ContentItemData = res.data.items
                console.log(this.ContentItemData)
            }).catch(res =>{
                console.log(res)
            })
        },
        handleChange(index) {
            this.swiperIndex = index
        },
        loadMore() {
            this.loading = true;
            setTimeout(() => {
                let last = this.ContentItemData-1;
                cosnoel.log(last)
                for (let i = 1; i <= 10; i++) {
                    this.ContentItemData.push(last + i);
                }
                this.loading = false;
            }, 2500);
        }
    }
}
</script>

<style scoped lang="less">
.content{
    max-width: 1170px;
    margin: 0 auto;
    margin-top: 16px;
    min-height: 1500px;
    display: flex;
    flex-direction: row;
    .banner{
        position: relative;
        width: 660px;
        height: 300px;
        .mint-swipe{
            width: 600px;
        }
        .my-indicators{
            
            position: absolute;
            color: #fff;
            right: 0;
            box-sizing: border-box; 
            top: 0;
            background: #000;
            height: 100%;
            margin: 0;
            padding: 7px 0;
            list-style: none;
            li{
                width: 60px;
                line-height: 36px;
                margin-bottom: 14px;
                cursor: pointer;
            }
            .indicator-active{
                position: relative;
                background: rgba(237,64,64,.8);
                
            }
            .indicator-active::before{
                    content: '';
                    position: absolute;
                    left: -6px;
                    top: 50%;
                    transform: translate(-50%, -50%);
                    width: 0;
                    height: 0;
                    border-bottom: 8px solid transparent;
                    border-top: 8px solid transparent;
                    border-right: 12px solid rgba(237, 64, 64, 0.8);
                }
        }
    }
}
</style>
