<template>
  <div>
    <div class="date-pickers">
      <div class="date-box">
        <!-- 操作栏 -->
        <div class="day-select">
          <div class="day-reduce">
            <span
              class="arrow-icon"
              @click="reduceYear"
            >
              <svg
                t="1685742878912"
                class="icon"
                viewBox="0 0 1024 1024"
                version="1.1"
                xmlns="http://www.w3.org/2000/svg"
                p-id="1530"
                width="16"
                height="16"
              >
                <path
                  d="M496.512 245.418667a42.666667 42.666667 0 0 0-56.32-64.170667l-303.744 266.581333a85.333333 85.333333 0 0 0 0.128 128.341334l304.64 266.624a42.666667 42.666667 0 1 0 56.234667-64.256L192.768 512l303.744-266.538667z"
                  fill="#303133"
                  p-id="1531"
                ></path>
                <path
                  d="M880.512 245.418667a42.666667 42.666667 0 0 0-56.32-64.170667l-303.744 266.581333a85.333333 85.333333 0 0 0 0.128 128.341334l304.64 266.624a42.666667 42.666667 0 1 0 56.234667-64.256L576.768 512l303.744-266.538667z"
                  fill="#303133"
                  p-id="1532"
                ></path>
              </svg>
            </span>
            <span
              class="arrow-icon"
              @click="reduceMonth"
            >
              <svg
                t="1685742835417"
                class="icon"
                viewBox="0 0 1024 1024"
                version="1.1"
                xmlns="http://www.w3.org/2000/svg"
                p-id="1216"
                width="16"
                height="16"
              >
                <path
                  d="M713.770667 185.173333a42.666667 42.666667 0 0 1-3.925334 60.245334l-303.786666 266.538666-28.16-32.085333 28.16 32.085333 304.725333 266.581334a42.666667 42.666667 0 1 1-56.192 64.256L349.866667 576.170667a85.333333 85.333333 0 0 1-0.085334-128.341334l303.786667-266.581333a42.666667 42.666667 0 0 1 60.16 3.925333z"
                  fill="#303133"
                  p-id="1217"
                ></path>
              </svg>
            </span>
          </div>
          <div class="day-cur">{{year}}年{{month}}月</div>
          <div class="day-add">
            <span
              class="arrow-icon"
              @click="addMonth"
            >
              <svg
                t="1685742855231"
                class="icon"
                viewBox="0 0 1024 1024"
                version="1.1"
                xmlns="http://www.w3.org/2000/svg"
                p-id="1372"
                width="16"
                height="16"
              >
                <path
                  d="M332.330667 185.173333a42.666667 42.666667 0 0 0 3.925333 60.245334L640 511.957333l28.16-32.085333L640 512l-304.682667 266.581333a42.666667 42.666667 0 0 0 56.192 64.256l304.682667-266.624a85.333333 85.333333 0 0 0 0.085333-128.341333L392.533333 181.248a42.666667 42.666667 0 0 0-60.202666 3.925333z"
                  fill="#303133"
                  p-id="1373"
                ></path>
              </svg>
            </span>
            <span
              class="arrow-icon"
              @click="addYear"
            >
              <svg
                t="1685742892519"
                class="icon"
                viewBox="0 0 1024 1024"
                version="1.1"
                xmlns="http://www.w3.org/2000/svg"
                p-id="1689"
                width="16"
                height="16"
              >
                <path
                  d="M506.922667 778.581333a42.666667 42.666667 0 1 0 56.32 64.170667l303.701333-266.581333a85.333333 85.333333 0 0 0-0.085333-128.341334l-304.64-266.624a42.666667 42.666667 0 1 0-56.234667 64.256L810.666667 512l-303.744 266.538667z"
                  fill="#303133"
                  p-id="1690"
                ></path>
                <path
                  d="M122.922667 778.581333a42.666667 42.666667 0 1 0 56.32 64.170667l303.701333-266.581333a85.333333 85.333333 0 0 0-0.085333-128.341334l-304.64-266.624a42.666667 42.666667 0 1 0-56.234667 64.256L426.666667 512l-303.744 266.538667z"
                  fill="#303133"
                  p-id="1691"
                ></path>
              </svg>
            </span>
          </div>
        </div>
        <!-- 内容栏 -->
        <div
          class="day-screen"
          :style="disabled ? 'filter: grayscale(1);' : ''"
        >
          <div class="day-week-item day-screen-item">
            <div
              v-for="weekItem in week"
              :key="weekItem"
              style="display: inline"
            >
              {{ weekItem }}
            </div>
          </div>
          <div class="day-screen-item day-content">
            <div
              v-for="pday in previousMonth"
              :key="`previousMonth-${pday}`"
              class="day-content-item"
            >
              <span
                class="day-gray"
                @click="selectDay($event, 'previousMonth')"
              >{{ pday }}</span>
            </div>
            <div
              v-for="mday in this.monthDay[month - 1]"
              :key="mday"
              class="day-content-item"
            >
              <span
                :class="isActive(mday)"
                class="currentMonth"
                @click="selectDay($event, 'currentMonth')"
              >{{mday}}</span>
            </div>
            <div
              v-for="nday in nextMonth"
              :key="`nextMonth-${nday}`"
              class="day-content-item"
            >
              <span
                class="day-gray"
                @click="selectDay($event, 'nextMonth')"
              >{{ nday }}</span>
            </div>
          </div>
        </div>
        <!-- 禁用时加遮罩层 -->
        <div
          v-if="disabled"
          class="day-wrap"
        ></div>
      </div>

    </div>
  </div>
</template>
<script>
export default {
  name: 'sta-date-picker',
  props: {
    value: {
      type: Array,
      default: () => []
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      year: 0,
      month: 0,
      day: 0,
      partialSelect: null,
      selctDate: [],
      previousMonth: [],
      nextMonth: [],
      week: ["日", "一", "二", "三", "四", "五", "六"],
      monthDay: [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31],
    }
  },
  computed: {
    date() {
      if (this.year === 0 || this.month === 0 || this.day === 0) {
        return ""
      }
      return `${this.year}/${this.month}/${this.day}`;
    }
  },
  watch: {
    value: {
      immediate: true,
      deep: true,
      handler(v) {
        this.selctDate = v;
      }
    },
    year: function (nv) {
      const reg = /^[1-9]\d*$/g
      if (!reg.test(nv)) {
        const date = new Date()
        this.year = date.getFullYear()
      }
      if (nv < 0) {
        this.year = 1
      }
      if (nv > 10000) {
        this.year = 10000
      }
      this.dayScreen()
    },
    month: function (nv) {
      const reg = /^[1-9]\d*$/g
      if (!reg.test(nv)) {
        const date = new Date()
        this.month = date.getMonth() + 1
      }
      if (nv < 1) {
        this.month = 1
      }
      if (nv > 12) {
        this.month = 12
      }
      this.dayScreen()
    }
  },
  created() {
    this.trueDateBox()
  },
  methods: {
    // 突出显示当前日期
    isActive(index) {
      const date = new Date()
      const y = date.getFullYear()
      const m = date.getMonth() + 1
      const d = date.getDate()
      const obj = {}

      if (this.year === y && this.month === m && index === d) {
        obj.today = true
      }
      const newIndexStr = index < 10 ? `0${index}` : `${index}`
      const newMonthStr = this.month < 10 ? `0${this.month}` : `${this.month}`
      const item = `${this.year}/${newMonthStr}/${newIndexStr}`
      if (item === this.partialSelect) {
        obj.active = true
      }
      if (this.selctDate.includes(item)) {
        obj.activeRange = true
      }
      return obj
    },
    // 初始化日期盒子并算好闰年平年
    trueDateBox() {
      if (this.date === "") {
        const date = new Date()
        this.year = date.getFullYear()
        this.updateLeapYear()
        this.month = date.getMonth() + 1
        this.day = null
      }
      this.dayScreen()
    },
    // 设置算好闰年平年
    updateLeapYear() {
      if (this.isLeapYear(this.year)) {
        this.monthDay[1] = 29
      } else {
        this.monthDay[1] = 28
      }
    },
    // 年份的增减
    addYear() {
      this.year++
      this.updateLeapYear()
    },
    reduceYear() {
      this.year--
      this.updateLeapYear()
    },
    // 月份的增减
    addMonth() {
      this.month++
      if (this.month > 12) {
        this.month = 1
        this.addYear()
      }
    },
    reduceMonth() {
      this.month--
      if (this.month < 1) {
        this.month = 12
        this.reduceYear()
      }
    },
    selectDay(e, type) {
      const iText = e.target.innerText
      const sDate = Number(iText) < 10 ? `0${iText}` : `${iText}`
      if (type === "previousMonth") {
        if (this.month === 1) {
          this.month = 12
          this.reduceYear()
        } else {
          this.month = this.month - 1
        }
      } else if (type === "nextMonth") {
        if (this.month === 12) {
          this.month = 1
          this.addYear()
        } else {
          this.month = this.month + 1
        }
      }

      let arr = this.selctDate.map((i) => new Date(i).getTime())
      const newMonthStr = this.month < 10 ? `0${this.month}` : `${this.month}`
      const curSelectTime = `${this.year}/${newMonthStr}/${sDate}`
      const curSelectTimeStamp = new Date(curSelectTime).getTime()
      const clsName = e.target.className // 通过类名判断当前是什么状态
      if (clsName.includes("activeRange")) {
        // 点击了范围内的数据，需要剔除
        arr = arr.filter((i) => i !== curSelectTimeStamp)
      } else if (clsName.includes("active") && !clsName.includes("activeRange")) {
        // 点击了一个半选状态的日期，准备扩展范围或者单选一个
        if (this.selctDate.length) {
          const itemTime = arr[0]
          const itemTime2 = arr[arr.length - 1]
          const selectTime = curSelectTimeStamp
          if (selectTime < itemTime) {
            console.log("点击了范围之前的时间")
          } else if (selectTime > itemTime2) {
            console.log("点击了范围之后的时间")
          } else {
            console.log("点击了范围内的空白，直接加上一个")
          }
          arr = [...arr, curSelectTimeStamp]
        } else {
          // 第一次选择日期，而且双击了，直接单独确定这个
          arr = [curSelectTimeStamp]
        }
        // 此时选择完日前了，半选的日期消费掉了，清空
        this.partialSelect = null
      } else {
        // 不是半选情况 即没有点击范围内，又不是半选状态，可能是已经存在一个半选，等待这个日期来闭合范围，也可能是第一次打开点击
        if (this.partialSelect) {
          // 需要和已存在的半选态日期闭合
          const itemTime = new Date(this.partialSelect).getTime()
          const itemTime2 = curSelectTimeStamp
          const timeArr = [itemTime, itemTime2].sort((a, b) => a - b) // 排序，因为不知道谁在前面
          for (let i = timeArr[0]; i <= timeArr[1]; i += 86400000) {
            arr.push(i)
          }
          // 此时确定好范围了，半选的日期消费掉了，清空
          this.partialSelect = null
        } else if (this.selctDate.length) {
          // 存在一个范围，同时点击范围外，此时设置半选
          this.day = sDate
          this.partialSelect = curSelectTime
        } else {
          // 不存在一个范围，所以是第一次点击
          this.day = sDate
          this.partialSelect = curSelectTime
        }
      }
      let filterArr = Array.from(new Set(arr))
      filterArr = filterArr.sort((a, b) => a - b)
      this.selctDate = filterArr.map((i) => this.formatTime(new Date(i)))
      this.$emit("input", this.selctDate)
      this.$emit("change", this.selctDate)
      this.day = parseInt(sDate)
    },
    // 日期显示
    dayScreen() {
      // 渲染上个月,第一行
      const firstDate = new Date(this.year, this.month - 1, 1)
      const firstWeek = firstDate.getDay()
      let preMonthDay = null
      if (this.month === 1) {
        preMonthDay = this.monthDay[11]
      } else {
        preMonthDay = this.monthDay[this.month - 2]
      };
      for (let i = 0; i < preMonthDay; i++) {
        this.previousMonth[i] = i + 1
      }
      if (firstWeek === 0) {
        this.previousMonth = this.previousMonth.slice(-7)
      } else {
        this.previousMonth = this.previousMonth.slice(-firstWeek)
      }

      // 渲染下个月, 最后一行
      const endDate = new Date(
        this.year,
        this.month - 1,
        this.monthDay[this.month - 1]
      )
      const endWeek = endDate.getDay()
      let nextMonthDay = null
      if (this.month === 12) {
        nextMonthDay = this.monthDay[0]
      } else {
        nextMonthDay = this.monthDay[this.month]
      }
      for (let i = 0; i < nextMonthDay; i++) {
        this.nextMonth[i] = i + 1
      }
      if (endWeek === 6) {
        this.nextMonth = this.nextMonth.slice(0, 7)
      } else {
        this.nextMonth = this.nextMonth.slice(0, 6 - endWeek)
      }
    },
    isLeapYear(year) {
      return year % 100 === 0 ? year % 400 === 0 : year % 4 === 0
    },
    formatTime(date = new Date(), format = "yyyy/MM/dd") {
      const args = {
        "M+": date.getMonth() + 1,
        "d+": date.getDate(),
        "h+": date.getHours(),
        "m+": date.getMinutes(),
        "s+": date.getSeconds(),
      }
      if (/(y+)/.test(format)) {
        format = format.replace(
          RegExp.$1,
          `${date.getFullYear()}`.substr(4 - RegExp.$1.length)
        )
      }
      for (const i in args) {
        const n = args[i]
        if (new RegExp(`(${i})`).test(format)) {
          format = format.replace(
            RegExp.$1,
            RegExp.$1.length === 1 ? n : `00${n}`.substr(`${n}`.length)
          )
        }
      }
      return format
    }
  }
};
</script>
<style scoped>
.date-pickers {
  position: relative;
}

.date-box {
  width: 322px;
  background: #fff;
}

.day-select {
  display: flex;
  padding: 5px 0;
  height: 30px;
  line-height: 30px;
  margin: 12px;
}
.day-select .day-reduce,
.day-select .day-add {
  width: 20%;
  text-align: center;
}
.day-select .day-reduce .arrow-icon {
  cursor: pointer;
  color: #ccc;
  font-size: 10px;
}
.day-select .day-reduce .arrow-icon:hover {
  color: #409eff;
}
.day-select .day-add .arrow-icon {
  cursor: pointer;
  color: #ccc;
  font-size: 10px;
}
.day-select .day-add .arrow-icon:hover {
  color: #409eff;
}
.day-select .day-cur {
  width: 60%;
  display: flex;
  justify-content: center;
}
.day-select .day-cur input:hover {
  background: #eee;
}
.day-select .day-cur input:nth-child(1) {
  width: 50px;
}
.day-select .day-cur input:nth-child(2) {
  width: 30px;
}

.day-screen {
  margin: 12px;
  position: relative;
}
.day-screen .day-screen-item div {
  width: 40px;
  height: 40px;
  line-height: 40px;
  text-align: center;
}

.day-screen .day-week-item {
  border-bottom: 1px solid #eee;
}

.day-screen .day-content .day-content-item {
  position: relative;
  display: inline;
}
.day-screen .day-content .day-content-item span {
  width: 24px;
  height: 24px;
  margin: 0 auto;
  line-height: 24px;
  display: block;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 15px;
}
.day-screen .day-content .day-content-item span:hover {
  font-weight: 700;
  background-color: #409eff;
  color: #fff;
}
.day-screen .day-content .day-content-item .active {
  font-weight: 700;
  background-color: #409eff;
  color: #fff;
}
.day-screen .day-content .day-content-item .today {
  color: #409eff;
  font-weight: 700;
}
.day-screen .day-content .day-content-item .activeRange {
  border-radius: 3px;
  background-color: #409eff;
  color: #fff;
}
.day-screen .day-content span {
  cursor: pointer;
  color: #000;
}
.day-screen .day-content .day-gray {
  color: #888;
}

.day-screen > div {
  padding: 0 5px;
  display: flex;
  font-size: 14px;
  justify-content: space-between;
  flex-wrap: wrap;
}

.day-wrap {
  width: 296px;
  height: 245px;
  position: absolute;
  left: 13px;
  top: 83px;
}
</style>