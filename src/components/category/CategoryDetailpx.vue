<template>
    <div class="ALl">
        <SearchBar></SearchBar>
        <headersec :tabname="changeText"></headersec>
        <div>
            <div class="my_wrap1">
                <div class="tab-item">
                    <!-- <router-link to='./SearchReslut'> -->
                     <router-link :to="{path: './CategoryDetail', query: {pxText: changeText,searchId: searchId}}">
                        <p class="tab-tite13">价格</p>
                    </router-link>
                </div>
                <div class="tab-item">
                    <router-link to='./CategoryDetailpx'>
                        <p class="tab-tite18">评论最多</p>
                    </router-link>
                </div>
            </div>
            <div style="background-color:#eee;  ">
                 <div v-if="productList">
                    <p class="noData">没有数据可加载</p>
                </div>
                <div v-if="!productList" class="wrap_goods" v-for="item in productList">
                    <div class="items">
                        <div class="img_avator">
                            <img class="img_a" :src="item.goods_image_path" alt="">
                        </div>
                        <div class="container_c">
                            <div>
                                <p>{{item.goods_name}}</p>
                            </div>
                            <div style="display: flex; margin-top:.1rem">
                                <p style="color:#E43448">{{item.goods_price}}</p>
                                元起
                            </div>
                        </div>
                    </div>
                    <div class="zz">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import SearchBar from '../base/SearchBar.vue';
    import Headersec from '../base/HeaderSec.vue';
    import {
        Header
    } from 'element-ui';
    export default {
        // props: ['tabname'],
        data() {
            return {
                isBack: true,
                isBack_detail: true,
                productList: [],
                changeText:'',
                titleText : '',
                searchId: null
            }
        },
        mounted() {
            this.changeText  = this.$route.query.changeText
            this.searchId = this.$route.query.searchId
            this.getProductList();
            
        },
        components: {
            Headersec,
            SearchBar
        },
        methods: {
            getProductList() {
    
                const that = this
                
                 this.$http
                    .get("/myapi/adel-shop/app/search.htm?orderBy=evaluates_size&gc_id=" +that.searchId)
                    .then(function(res) {
                        that.productList = res.data.data.goodsList
                    })
                    .catch(function(error) {});
            }
        }
    }
</script>

<style>
    .mycontainer {
        display: flex;
        background-color: #E43448;
        align-items: center;
        height: .8rem;
    }
    .my_wrap1 {
        margin-top: .2rem;
        width: 100%;
        display: flex;
    }
    .tab-item {
        flex: 1;
        display: flex;
        justify-content: center;
        font-size: .26rem;
        align-items: center;
    }
    .tab-item p {
        padding-bottom: .2rem;
    }
    .tab-tite13 {
      color: black;
        padding-bottom: .1rem;
        box-sizing: border-box;
    }
    .tab-tite18{
                color: red;
        padding-bottom: .1rem;
        box-sizing: border-box;
        border-bottom: .01rem solid red!important
  
    }
    .img_back {
        width: .4rem;
        height: .4rem;
        flex: 1;
    }
    .input {
        width: 70%;
        height: .6rem;
        font-size: .3rem;
        border-radius: .1rem;
        flex: 9
    }
    .searchbar {
        color: white;
        font-size: .25rem;
        padding-left: .2rem;
        flex: 1
    }
    .my_wrap {
        margin-top: 1rem;
        width: 100%;
        display: flex;
    }
    .tab-item {
        flex: 1;
        display: flex;
        justify-content: center;
        font-size: .26rem;
        align-items: center;
    }
    .tab-item p {
        padding-bottom: .2rem;
    }
    .tab-tite2 {
        color: red;
        padding-bottom: .1rem;
        box-sizing: border-box;
        border-bottom: .01rem solid red!important
    }
    .tab-tite6 {
        color: black;
        padding-bottom: .1rem;
        box-sizing: border-box;
    }
    .container_c {
        display: flex;
        flex-direction: column;
        /* align-items: center; */
        margin-left: .3rem;
        justify-content: center;
    }
    .slopingside1 {
        border: 1px solid red;
        -o-transform: rotate(125deg);
        -moz-transform: rotate(125deg);
        -webkit-transform: rotate(10deg);
        position: absolute;
        width: .8rem;
        margin-top: .16rem;
    }
    .linear {
        height: 0px;
        border: 1px solid red;
        margin-left: 30px;
        margin-top: -10px;
    }
    .seckillhaveget1 {
        display: flex;
        flex: 1;
        color: #E43448;
        background-color: #fff;
        border-bottom: .02rem solid #E43448;
    }
    .wrap_container {
        display: flex;
        justify-content: space-between;
        margin-top: .9rem;
        height: .9rem;
        margin-top: .82rem;
        position: fixed;
        width: 100%;
        z-index: 2;
    }
    .seckillBeging2 {
        display: flex;
        flex: 1;
        color: #E43448;
        background-color: #eee;
    }
    .wrap_goods {
        background-color: #fff;
    }
    .baby {
        display: flex;
        width: 100%;
        justify-content: space-between;
        align-items: center;
        padding: 0 .2rem;
    }
    .bor_raid {
        width: 2.5rem;
        height: .3rem;
        border-radius: .1rem;
        border: .01rem solid #E43448
    }
    .comming {
        font-size: 0.3rem;
        display: flex;
        justify-content: center;
        font-size: .3rem
    }
    .robbot {
        display: flex;
        justify-content: flex-end
    }
    .robbot1 {
        display: flex;
        border-radius: 1rem;
        color: #fff;
        width: .5rem;
        height: .5rem;
        background-color: #E43448;
        justify-content: flex-end;
        justify-content: center;
        align-items: center;
    }
    .wapr {
        width: 100%
    }
    .img_avator {
        display: flex;
        align-items: center
    }
    .img_a {
        width: 1.2rem;
        height: 1.2rem;
    }
    .zz {
        height: .25rem;
        background-color: #eee
    }
    .items {
        display: flex;
        padding: 0 .2rem;
        font-size: .26rem;
        height: 1.5rem;
    }
    .time {
        font-size: .26rem;
        display: flex;
        align-items: center;
        padding: 0 .1rem;
        padding-right: .2rem;
    }
</style>

