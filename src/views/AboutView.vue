<template lang="">
    <ul class="tabs">
        <!--  <li class="tab" @click="changeTab(0)">會員中心</li>
        <li class="tab" @click="changeTab(1)">訂單資訊</li>
        <li class="tab" @click="changeTab(2)">優惠券</li>
        <li class="tab" @click="changeTab(3)">認養紀錄</li> -->
        <li
            class="tab"
            v-for="(tabItem, index) in tabGroup"
            @click="changeTab(index)"
        >
            {{ tabItem }}
        </li>
    </ul>

    <div class="wrapper">
        <div class="test" :style="{ left: `-${currentTab}%` }">
            <div class="item member">
                <div>我是會員中心</div>
            </div>
            <div class="item order">我是訂單資訊</div>
            <div class="item discont">我是優惠券</div>
            <div class="item adopt">我是認養紀錄</div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            tabGroup: ["會員中心", "訂單資訊", "優惠券", "認養紀錄"],
            currentTab: 0,
        };
    },
    methods: {
        changeTab(tab) {
            console.log("test");
            this.currentTab = tab * 100;
        },
    },
};
</script>
<style lang="scss">
.tabs {
    display: flex;
    list-style: none;
    justify-content: center;
    margin-top: 100px;
    .tab {
        padding: 20px;
        cursor: pointer;
    }
}
.wrapper {
    background-color: #39c5bb;
    width: 300px;
    margin: auto;
    overflow: hidden;
    color: #f7f7f7;
    flex-wrap: nowrap;
    .test {
        display: flex;
        position: relative;
        transition: left 0.3s linear;
        .item {
            width: 100%;
            flex-shrink: 0;
        }
    }
}
</style>
