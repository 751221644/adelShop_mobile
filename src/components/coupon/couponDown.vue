<template>
    <div>
        <headersec tabname="优惠券"  ref="noback"></headersec>
        <CouponTab :urlRouter="$route.path"></CouponTab>
        <div style="height:2rem"></div>
        <div class="coupon_container1" v-for="couponItem in CouponList">
            <div class="top">
                <div class="top_money">
                    <p style="font-size:.3rem;">{{couponItem.coupon_name}}</p>
                    <p style="font-size:.45rem;">¥ {{couponItem.coupon_amount}}</p>
                </div>
                <div class="used">
                    <p v-show="couponItem.class_name">{{couponItem.class_name}}</p>
                    <p v-show="!couponItem.class_name">全场通用</p>
                    <p>（满{{couponItem.coupon_order_amount}}元可用）</p>
                </div>
            </div>
            <div class="foot1">
                <div class="foot_time1">
                    <p>有效期：{{couponItem.coupon_begin_time}} 至 {{couponItem.coupon_end_time}}</p>
                </div>
            </div>
              <div>
            <img class="img_used1" src="../../../static/img/ade_shop/expired.png" />
        </div>
        </div>
      
        <div class="toGetconpon" @click="toAllCoupon">
            <p>去领券</p>
        </div>
    </div>
</template>

<script>
    import Headersec from '../base/HeaderSec.vue';
    import CouponTab from '../base/CouponTab.vue'
    export default {
        components: {
            Headersec,
            CouponTab
        },
        data() {
            return {
                status: -1,
                CouponList: {}
            }
        },
        mounted() {
			this.$refs.noback.isBack = false
            this.getconponList();
        },
        methods: {
            getconponList() {
                console.log('111');
                const that = this;
                this.$http
                    .get("/myapi/adel-shop/app/auth/getUserCoupon.htm?status=" + this.status)
                    .then(function(res) {
                        console.log('get', res.data.data)
                        that.CouponList = res.data.data.couponList
                    })
                    .catch(function(error) {});
            },
            toAllCoupon() {
                this.$router.push("./allCoupon");
                //   this.$router.push("../coupon/allCoupon");
            }
        }
    }
</script>

<style>
    .used {
        font-size: .25rem;
        padding-top: .25rem;
        display: flex;
        justify-content: space-between;
    }
    .coupon_container1 {
        padding-bottom: .3rem
    }
    .img_used1 {
        width: 1rem;
        height: 1rem;
        position: absolute;
        right: .5rem;
        top: 3.05rem;
    }
    .toGetconpon {
        background-color: #EE2C2C;
        position: absolute;
        bottom: 0;
        width: 100%;
        height: 0.68rem;
        display: flex;
        align-items: center;
        justify-content: center;
        color: #fff;
        font-size: 0.25rem;
    }
    .img_tab1 {
        position: absolute;
        top: 1.05rem;
        right: .5rem;
    }
    .top {
        background-color: #EE2C2C;
        height: 1.5rem;
        padding: 0 .3rem;
        color: #fff;
    }
    .top_money {
        padding-top: 0.2rem;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .foot_time1 {
        background-color: #fff;
        height: .7rem;
        display: flex;
        align-items: center;
        padding: 0 .3rem;
        font-size: .25rem;
    }
    body {
        background-color: #eee
    }
</style>
