<template>
  <div class="home">
    <div class="container">
      <div class="nav">
        <div class="top">
          <h2>預約行事曆</h2>
          <div class="content-show">
            <button>周檢視</button>
            <button>莉</button>
          </div>
        </div>
        <div class="bottom">
          <div class="cal-icon">
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
        <div class="week" v-for="i in 24" :key="i.id">
          <p>{{ i }} :00 am</p>

          <div class="day" v-for="j in 8" :key="j.id"></div>
        </div>
      </div>
      <div class="cal-bottom">
        <button>+ 新增預約</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      today: {
        year: 0,
        month: 0,
        date: 0,
        day: 0,
      },
      calendar: {
        year: 0,
        month: 0,
        date: 0,
        day: 0,
      },
    };
  },

  created() {
    const date = new Date();
    this.today.year = this.calendar.year = date.getFullYear();
    this.today.month = this.calendar.month = date.getMonth();
    this.today.date = this.calendar.date = date.getDate();
    this.today.day = this.calendar.day = date.getDay();
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

.cal-middle .week {
  display: flex;
  position: relative;
}

.cal-middle .week p {
  white-space: nowrap;
  font-size: 10px;
  align-items: center;
  position: absolute;
  bottom: -8px;
  left: 3px;
}

.cal-middle .week .day {
  width: 12%;
  height: 50px;
  border-right: 1px #e0e0e0 solid;
  border-bottom: 1px #e0e0e0 solid;
  display: flex;
}

.cal-middle .week .day:nth-child(2) {
  width: calc(100% - (12% * 7));
}

.cal-middle .week .day:nth-child(9) {
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
</style>