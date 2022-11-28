<template lang="">
    <div class="book-from">
        <button class="close-btn" @click="closeBookTab">關閉</button>
        <h1>預約資訊</h1>
        <form>
            <div class="inputbox">
                <label for="name">姓名</label>
                <input type="text" name="name" id="name" />
            </div>
            <div class="inputbox">
                <label for="phone">電話</label>
                <input type="text" name="phone" id="phone" />
            </div>
            <div class="inputbox">
                <label for="email">Email</label>
                <input type="email" name="email" id="email" />
            </div>
            <div class="inputbox">
                <label for="date">預約日期</label>
                <input
                    v-model="bookDate"
                    type="text"
                    name="date"
                    id="date"
                    disabled="disabled"
                />
            </div>
            <button>送出</button>
        </form>
    </div>
</template>
<script>
export default {
    props: ["msg"],
    data() {
        return {
            bookDate: this.msg,
        };
    },
    methods: {
        closeBookTab() {
            this.$emit("update", false);
        },
    },
};
</script>

<style>
.book-from {
    width: 800px;
    height: 600px;
    padding: 100px 100px;
    background-color: #39c5bb;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
.close-btn {
    position: absolute;
    top: 0;
    right: 0;
}
.inputbox {
    margin-bottom: 20px;
}
</style>
