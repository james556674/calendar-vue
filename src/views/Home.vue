<template>
  <div class="home">
    <div class="container" v-show="weekShow">
      <div class="nav">
        <div class="top">
          <h2>預約行事曆</h2>
          <div class="content-show">
            <button v-on:click.stop.prevent="showDay">日檢視</button>
            <button>莉</button>
          </div>
        </div>
        <div class="bottom">
          <div class="cal-icon" v-on:click.stop.prevent="showMonth">
            <font-awesome-icon
              class="cal-icon-svg"
              :icon="['far', 'calendar']"
            />
          </div>
          <div class="cal-show">
            <div class="cal-wrapper">
              <div class="day">M</div>
              <div class="date">01</div>
            </div>
            <div class="cal-wrapper">
              <div class="day">T</div>
              <div class="date">02</div>
            </div>
            <div class="cal-wrapper">
              <div class="day">W</div>
              <div class="date">03</div>
            </div>
            <div class="cal-wrapper">
              <div class="day">T</div>
              <div class="date">04</div>
            </div>
            <div class="cal-wrapper">
              <div class="day">F</div>
              <div class="date">05</div>
            </div>
            <div class="cal-wrapper">
              <div class="day">S</div>
              <div class="date">06</div>
            </div>
            <div class="cal-wrapper">
              <div class="day">S</div>
              <div class="date">07</div>
            </div>
          </div>
        </div>
      </div>
      <div class="cal-middle">
        <div class="time" v-for="(time, index) in daytimes" :key="index">
          <p>{{ time }} :00 am</p>

          <div class="day" v-for="(j, index) in 8" :key="index"></div>
        </div>
      </div>
      <div class="cal-bottom">
        <button>+ 新增預約</button>
      </div>
    </div>
    <div class="container" v-show="dayShow">
      <div class="nav">
        <div class="top">
          <div class="right-side">
            <div class="left-arrow" v-on:click.stop.prevent="dateDown()"></div>
            <div class="current-date">
              {{ this.currentDate.year }}/ {{ this.currentDate.month + 1 }}/
              {{ this.currentDate.date }}
            </div>
            <div class="right-arrow" v-on:click.stop.prevent="dateUp()"></div>
          </div>

          <div class="content-show">
            <button v-on:click.stop.prevent="showWeek">周檢視</button>
            <button>莉</button>
          </div>
        </div>
        <div class="bottom">
          <div class="cal-icon" v-on:click.stop.prevent="showMonth">
            <font-awesome-icon
              class="cal-icon-svg"
              :icon="['far', 'calendar']"
            />
          </div>
          <div class="cal-show">
            <div class="cal-wrapper">
              <div class="day">M</div>
              <div class="date">01</div>
            </div>
            <div class="cal-wrapper">
              <div class="day">T</div>
              <div class="date">02</div>
            </div>
            <div class="cal-wrapper">
              <div class="day">W</div>
              <div class="date">03</div>
            </div>
            <div class="cal-wrapper">
              <div class="day">T</div>
              <div class="date">04</div>
            </div>
            <div class="cal-wrapper">
              <div class="day">F</div>
              <div class="date">05</div>
            </div>
            <div class="cal-wrapper">
              <div class="day">S</div>
              <div class="date">06</div>
            </div>
            <div class="cal-wrapper">
              <div class="day">S</div>
              <div class="date">07</div>
            </div>
          </div>
        </div>
      </div>
      <div class="cal-middle">
        <div class="time" v-for="(time, index) in daytimes" :key="index">
          <p>{{ time }} :00 am</p>

          <div class="one-day" v-for="(j, index) in 2" :key="index"></div>
        </div>
      </div>
      <div class="cal-bottom">
        <button>+ 新增預約</button>
      </div>
    </div>
    <div class="container month" v-show="monthShow">
      <div class="nav">
        <div class="top-side">
          <div class="left-side">
            <div class="cal-icon">
              <font-awesome-icon
                class="cal-icon-svg"
                :icon="['far', 'calendar']"
              />
            </div>
            <h2>選擇日期</h2>
          </div>
          <div class="right">
            <div class="cancel-btn" v-on:click.stop.prevent="showMonth">X</div>
          </div>
        </div>
        <div class="bottom-side">
          <div class="cal-show">
            <div
              class="cal-wrapper"
              v-for="(weekday, index) in weekdays"
              :key="index"
            >
              {{ weekday }}
            </div>
          </div>
        </div>
      </div>
      <div class="cal-middle">
        <div v-for="(i, index) in month" :key="index">
          2020/ {{ index + 1 }}
          <div class="date">
            <div
              class="day"
              v-for="(n, index) in currentMonthDays"
              :key="'day' + index"
            >
              {{ n }}
            </div>
            <div
              class="day-hidden"
              v-for="(n, index) in 36 - (currentMonthDays + firstMonthDay)"
              :key="'next' + index"
            >
              {{ n }}
            </div>
          </div>
        </div>
      </div>
      <div class="cal-bottom">
        <button>選擇</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      daytimes: [
        1,
        2,
        3,
        4,
        5,
        6,
        7,
        8,
        9,
        10,
        11,
        12,
        13,
        14,
        15,
        16,
        17,
        18,
        19,
        20,
        21,
        22,
        23,
        24,
      ],
      currentDate: {
        date: 0,
        month: 0,
        year: 0,
      },
      weekdays: ["M", "T", "W", "T", "F", "S", "S"],
      weekdayNames: [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ],
      month: [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ],

      dayShow: false,
      weekShow: true,
      monthShow: false,
    };
  },

  created() {
    this.getToday();
  },
  computed: {
    prevMonthDays() {
      let year =
        this.currentDate.month === 0
          ? this.currentDate.year - 1
          : this.currentDate.year;
      let month = this.currentDate.month === 0 ? 12 : this.currentDate.month;
      return new Date(year, month, 0).getDate();
    },
    firstMonthDay() {
      let firstDay = new Date(
        this.currentDate.year,
        this.currentDate.month,
        1
      ).getDay();
      if (firstDay === 0) firstDay = 7;
      return firstDay;
    },
    currentDay() {
      return new Date(
        this.currentDate.year,
        this.currentDate.month,
        this.currentDate.date
      ).getDay();
    },
    currentMonthDays() {
      return new Date(
        this.currentDate.year,
        this.currentDate.month + 1,
        0
      ).getDate();
    },
  },
  methods: {
    getToday() {
      let today = new Date();
      this.currentDate.date = today.getDate();
      this.currentDate.month = today.getMonth();
      this.currentDate.year = today.getFullYear();
    },
    dateUp() {
      if (this.currentDate.date === this.currentMonthDays) {
        this.currentDate.date = 1;
        this.monthUp();
      } else {
        this.currentDate.date += 1;
      }
    },
    dateDown() {
      if (this.currentDate.date === 1) {
        this.currentDate.date = this.prevMonthDays;
        this.monthDown();
      } else {
        this.currentDate.date -= 1;
      }
    },
    monthUp() {
      if (this.currentDate.month === 11) {
        this.currentDate.month = 0;
        this.currentDate.year += 1;
      } else {
        this.currentDate.month += 1;
      }
    },
    monthDown() {
      if (this.currentDate.month === 0) {
        this.currentDate.month = 11;
        this.currentDate.year -= 1;
      } else {
        this.currentDate.month -= 1;
      }
    },
    showMonth() {
      if (this.monthShow === true) {
        this.monthShow = false;
        this.weekShow = true;
      } else {
        this.monthShow = true;
        this.weekShow = false;
        this.dayShow = false;
      }
    },
    showDay() {
      (this.dayShow = true), (this.weekShow = false);
    },
    showWeek() {
      (this.dayShow = false), (this.weekShow = true);
    },
  },
};
</script>

<style scoped>
.container {
  width: 375px;
  min-height: 667px;
  background: #fcfcfc;
  margin: auto;
}

.nav {
  width: 100%;
  height: 90px;
  background: #ffffff;
  -webkit-box-shadow: 0px 2px 12px 0px rgba(0, 0, 0, 0.1);
  -moz-box-shadow: 0px 2px 12px 0px rgba(0, 0, 0, 0.1);
  box-shadow: 0px 2px 12px 0px rgba(0, 0, 0, 0.1);
  padding-bottom: 1rem;
}

.nav .top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 50px;
}

.nav .top .right-side {
  margin-left: 1rem;
  display: flex;
  align-items: center;
}
.nav .top .right-side .left-arrow,
.nav .top .right-side .right-arrow {
  height: 20px;
  width: 20px;
  background: #9d9d9d;
  margin-right: 1rem;
  margin-left: 0.5rem;
  border-radius: 50%;
  line-height: 20px;
  cursor: pointer;
}
.nav .top .right-side .left-arrow::after {
  content: "<";
  color: white;
}

.nav .top .right-side .right-arrow::after {
  content: ">";
  color: white;
}

.nav .top h2 {
  margin-left: 1rem;
}

.nav .top .content-show button {
  background: #dedaf4;
  height: 30px;
  min-width: 40px;
  border-radius: 50px;
  margin-right: 1rem;
  border: none;
  color: #7f74b4;
  font-size: 12px;
  position: relative;
  padding-right: 25px;
  padding-left: 15px;
  cursor: pointer;
}

.nav .top .content-show button::after {
  content: "";
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  right: 10%;
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 5px 5px 0 5px;
  border-color: #7f74b4 transparent transparent transparent;
}

.nav .bottom {
  display: flex;
  align-items: center;
  justify-content: center;
}

.nav .bottom .cal-icon {
  background: #dedaf4;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  line-height: 30px;
}

.nav .bottom .cal-icon .cal-icon-svg {
  color: #7f74b4;
}

.nav .bottom .cal-show {
  display: flex;
}

.nav .bottom .cal-show .cal-wrapper {
  margin-left: 1.7rem;
}

.cal-middle {
  background: transparent;
  height: 600px;
  overflow: scroll;
  width: 100%;
  margin-top: 1rem;
}

.cal-middle .time {
  display: flex;
  position: relative;
}

.cal-middle .time p {
  white-space: nowrap;
  font-size: 10px;
  align-items: center;
  position: absolute;
  bottom: -8px;
  left: 3px;
}

.cal-middle .time .day {
  width: 12%;
  height: 50px;
  border-right: 1px #e0e0e0 solid;
  border-bottom: 1px #e0e0e0 solid;
  display: flex;
}

.cal-middle .time .one-day:nth-child(2) {
  width: 15%;
  height: 50px;
  border-right: 1px #e0e0e0 solid;
  border-bottom: 1px #e0e0e0 solid;
  display: flex;
}

.cal-middle .time .one-day:nth-child(3) {
  width: 85%;
  height: 50px;
  border-bottom: 1px #e0e0e0 solid;
  display: flex;
}

.cal-middle .time .day:nth-child(2) {
  width: calc(100% - (12% * 7));
}

.cal-middle .time .day:nth-child(9) {
  border-right: none;
  border-bottom: 1px #e0e0e0 solid;
}

.cal-bottom button {
  background: #7f74b4;
  height: 40px;
  width: 120px;
  border-radius: 14%;
  border: none;
  color: white;
  font-size: 12px;
  cursor: pointer;
  position: fixed;
  bottom: 5%;
  left: 50%;
  transform: translateX(-50%);
  -webkit-box-shadow: 0px 1px 5px 0px rgba(87, 87, 87, 1);
  -moz-box-shadow: 0px 1px 5px 0px rgba(87, 87, 87, 1);
  box-shadow: 0px 1px 5px 0px rgba(87, 87, 87, 1);
}

/* 月顯示 */
.month .nav .top-side {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 1rem;
}

.month .nav .top-side .left-side {
  display: flex;
  align-items: center;
}

.month .nav .top-side .left-side .cal-icon {
  background: #dedaf4;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  line-height: 30px;
  margin-right: 1rem;
}

.month .nav .top-side .left-side .cal-icon .cal-icon-svg {
  color: #7f74b4;
}

.month .nav .bottom-side .cal-show {
  display: flex;
  justify-content: space-evenly;
  font-weight: 600;
}

.month .cal-middle .date {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(33px, 1fr));
  grid-gap: 10px;
  padding: 10px 23px 23px;
}
.month .cal-middle .date div {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 30px;
  color: black;
  border-radius: 5px;
}

.month .cal-middle .date .day-hidden {
  opacity: 0.4;
}
</style>