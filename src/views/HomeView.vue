<template>
    <div class="dd">
        <Calendar
            :cell-height="100"
            :first-day-of-week="7"
            class="ivu-text-right"
        >
            <template #month="{ date, data }">
                <div>
                    <CellGroup>
                        <Cell
                            class="ivu-text-center ivu-p-16"
                            v-if="dateQQ[data.day]"
                            :title="dateQQ[data.day]"
                            disabled
                        />
                        <Cell
                            class="ivu-text-center ivu-p-16"
                            v-else-if="isBefore(data.day)"
                            title="可預約"
                            @click="book(data.day)"
                        />
                    </CellGroup>
                </div>
            </template>
        </Calendar>
        <book-view :msg="bd" v-if="isBooking" @update="close"></book-view>
    </div>
</template>
<script>
import dayjs from "dayjs";
import BookView from "./BookView.vue";
const isBetween = require("dayjs/plugin/isBetween");
dayjs.extend(isBetween);

export default {
    components: {
        BookView,
    },
    data() {
        return {
            dateQQ: {
                "2022-11-05": "休館",
                "2022-11-06": "休館",
                "2022-11-09": "已預約",
                "2022-11-11": "已預約",
                "2022-11-12": "休館",
                "2022-11-13": "休館",
                "2022-11-19": "休館",
                "2022-11-20": "休館",
                "2022-11-23": "已預約",
                "2022-11-25": "已預約",
                "2022-11-26": "休館",
                "2022-11-27": "休館",
                "2022-12-03": "休館",
                "2022-12-04": "休館",
                "2022-12-10": "休館",
                "2022-12-11": "休館",
                "2022-12-17": "休館",
                "2022-12-18": "休館",
                "2022-12-24": "休館",
                "2022-12-25": "休館",
                "2022-12-31": "休館",
            },
            bd: "",
            isBooking: false,
        };
    },
    methods: {
        book(day) {
            this.bd = day;
            this.isBooking = true;
        },
        isBefore(day) {
            let dayArr = day.split("-");
            let [Y, M, D] = dayArr;
            const d = new Date(Y, +M - 1, D);
            return (
                dayjs(d).isBetween("2022-11-01", "2022-11-30", "day", "[]") &&
                dayjs().isBefore(day)
            );
        },
        close(val) {
            this.isBooking = val;
        },
    },
};
</script>
