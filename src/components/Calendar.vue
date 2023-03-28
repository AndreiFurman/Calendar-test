<template>
  <div class="ne-calendar-holder">
    <div class="ne-calendar">
      <tr class="ne-calendar-pick">
        <a href="#" class="nav-arrow" @click="decrease">
          <svg class="icon-arrow left" width="10" height="6" viewBox="0 0 10 6" fill="none"
               xmlns="http://www.w3.org/2000/svg">
            <path
                d="M1.53246 0.2661L5.00466 3.80169L8.47687 0.2661C8.55972 0.181736 8.65808 0.114815 8.76633 0.0691577C8.87458 0.0235002 8.9906 8.88921e-10 9.10777 0C9.22494 -8.88916e-10 9.34096 0.0235002 9.44921 0.0691577C9.55746 0.114815 9.65582 0.181736 9.73867 0.2661C9.82152 0.350464 9.88724 0.450618 9.93208 0.560845C9.97692 0.671072 10 0.789212 10 0.908521C10 1.02783 9.97692 1.14597 9.93208 1.2562C9.88724 1.36642 9.82152 1.46658 9.73867 1.55094L5.63109 5.73351C5.5483 5.81799 5.44996 5.88501 5.3417 5.93074C5.23345 5.97646 5.11739 6 5.00019 6C4.88299 6 4.76693 5.97646 4.65868 5.93074C4.55042 5.88501 4.45208 5.81799 4.36929 5.73351L0.261707 1.55094C0.178747 1.46664 0.112929 1.36651 0.0680222 1.25627C0.023115 1.14604 0 1.02786 0 0.908521C0 0.789178 0.023115 0.671007 0.0680222 0.560771C0.112929 0.450536 0.178747 0.350402 0.261707 0.2661C0.610717 -0.0801698 1.18345 -0.0892821 1.53246 0.2661Z"
                fill="#AFAFAF"/>
          </svg>
        </a>
        <div class="month-pick">{{ mapMonth[month] }}</div>
        <a href="#" class="nav-arrow" @click="increase">
          <svg class="icon-arrow right" width="10" height="6" viewBox="0 0 10 6" fill="none"
               xmlns="http://www.w3.org/2000/svg">
            <path
                d="M1.53246 0.2661L5.00466 3.80169L8.47687 0.2661C8.55972 0.181736 8.65808 0.114815 8.76633 0.0691577C8.87458 0.0235002 8.9906 8.88921e-10 9.10777 0C9.22494 -8.88916e-10 9.34096 0.0235002 9.44921 0.0691577C9.55746 0.114815 9.65582 0.181736 9.73867 0.2661C9.82152 0.350464 9.88724 0.450618 9.93208 0.560845C9.97692 0.671072 10 0.789212 10 0.908521C10 1.02783 9.97692 1.14597 9.93208 1.2562C9.88724 1.36642 9.82152 1.46658 9.73867 1.55094L5.63109 5.73351C5.5483 5.81799 5.44996 5.88501 5.3417 5.93074C5.23345 5.97646 5.11739 6 5.00019 6C4.88299 6 4.76693 5.97646 4.65868 5.93074C4.55042 5.88501 4.45208 5.81799 4.36929 5.73351L0.261707 1.55094C0.178747 1.46664 0.112929 1.36651 0.0680222 1.25627C0.023115 1.14604 0 1.02786 0 0.908521C0 0.789178 0.023115 0.671007 0.0680222 0.560771C0.112929 0.450536 0.178747 0.350402 0.261707 0.2661C0.610717 -0.0801698 1.18345 -0.0892821 1.53246 0.2661Z"
                fill="#AFAFAF"/>
          </svg>
        </a>
        <a href="#" class="nav-arrow" @click="prevYear">
          <svg class="icon-arrow left" width="10" height="6" viewBox="0 0 10 6" fill="none"
               xmlns="http://www.w3.org/2000/svg">
            <path
                d="M1.53246 0.2661L5.00466 3.80169L8.47687 0.2661C8.55972 0.181736 8.65808 0.114815 8.76633 0.0691577C8.87458 0.0235002 8.9906 8.88921e-10 9.10777 0C9.22494 -8.88916e-10 9.34096 0.0235002 9.44921 0.0691577C9.55746 0.114815 9.65582 0.181736 9.73867 0.2661C9.82152 0.350464 9.88724 0.450618 9.93208 0.560845C9.97692 0.671072 10 0.789212 10 0.908521C10 1.02783 9.97692 1.14597 9.93208 1.2562C9.88724 1.36642 9.82152 1.46658 9.73867 1.55094L5.63109 5.73351C5.5483 5.81799 5.44996 5.88501 5.3417 5.93074C5.23345 5.97646 5.11739 6 5.00019 6C4.88299 6 4.76693 5.97646 4.65868 5.93074C4.55042 5.88501 4.45208 5.81799 4.36929 5.73351L0.261707 1.55094C0.178747 1.46664 0.112929 1.36651 0.0680222 1.25627C0.023115 1.14604 0 1.02786 0 0.908521C0 0.789178 0.023115 0.671007 0.0680222 0.560771C0.112929 0.450536 0.178747 0.350402 0.261707 0.2661C0.610717 -0.0801698 1.18345 -0.0892821 1.53246 0.2661Z"
                fill="#AFAFAF"/>
          </svg>
        </a>
        <div>{{ year }}</div>
        <a href="#" class="nav-arrow" @click="nextYear">
          <svg class="icon-arrow right" width="10" height="6" viewBox="0 0 10 6" fill="none"
               xmlns="http://www.w3.org/2000/svg">
            <path
                d="M1.53246 0.2661L5.00466 3.80169L8.47687 0.2661C8.55972 0.181736 8.65808 0.114815 8.76633 0.0691577C8.87458 0.0235002 8.9906 8.88921e-10 9.10777 0C9.22494 -8.88916e-10 9.34096 0.0235002 9.44921 0.0691577C9.55746 0.114815 9.65582 0.181736 9.73867 0.2661C9.82152 0.350464 9.88724 0.450618 9.93208 0.560845C9.97692 0.671072 10 0.789212 10 0.908521C10 1.02783 9.97692 1.14597 9.93208 1.2562C9.88724 1.36642 9.82152 1.46658 9.73867 1.55094L5.63109 5.73351C5.5483 5.81799 5.44996 5.88501 5.3417 5.93074C5.23345 5.97646 5.11739 6 5.00019 6C4.88299 6 4.76693 5.97646 4.65868 5.93074C4.55042 5.88501 4.45208 5.81799 4.36929 5.73351L0.261707 1.55094C0.178747 1.46664 0.112929 1.36651 0.0680222 1.25627C0.023115 1.14604 0 1.02786 0 0.908521C0 0.789178 0.023115 0.671007 0.0680222 0.560771C0.112929 0.450536 0.178747 0.350402 0.261707 0.2661C0.610717 -0.0801698 1.18345 -0.0892821 1.53246 0.2661Z"
                fill="#AFAFAF"/>
          </svg>
        </a>
      </tr>
      <table class="table">
        <thead>
        </thead>
        <tr class="ne-calendar-dayWeek-holder">
          <td class="ne-calendar-dayWeek" v-for="d in day">{{ d }}</td>
        </tr>
        <tbody>
        <tr v-for="week in calendar()">
          <td class="ne-calendar-day"
              @click="datePick=year+'-'+(Number(month)+1)+'-'+day.index"
              v-for="(day, index) in week"
              :class="{disabled:!day.index, event:eventDay(day.index), active: year+'-'+month+'-'+day.index == date, picked:year+'-'+(Number(month)+1)+'-'+day.index == datePick}">
            {{ day.index }}
          </td>
        </tr>
        </tbody>
      </table>
    </div>
    <TransitionExpand>
      <div class="event-holder" v-show="datePick!==''">

        <div class="event-list" v-for="event in eventFilter" v-if="eventFilter.length!==0">
          <h3>Event description</h3>
          <div>{{event.text}}</div>

          <div class="event-time-holder">
            <h3>Event time</h3>
            <div class="event-time">{{moment(event.start).tz("Europe/London").format("DD-MM-YYYY")}} {{moment(event.start).tz("Europe/London").format("HH:mm")}} - {{moment(event.end).tz("Europe/London").format("HH:mm")}} (Europe/London)</div>
          </div>
        </div>
        <div v-if="eventFilter.length===0">
          <h3>No events for this date</h3>
        </div>
        <a class="button plus" @click="openModal">
          <span class="bg" id="plus"></span>
          <span class="symbol"></span>
        </a>
      </div>
    </TransitionExpand>
    <Modal ref="modal_add">
      <template slot="modal">
        <h3>Add description</h3>
        <textarea v-model="description" class="textarea-modal" rows="5"></textarea>
        <div class="time-holder">
          <div>
          <h3>Start time</h3>
          <vue-timepicker v-model="start" format="HH:mm"></vue-timepicker>
          </div>
          <div>
          <h3>End time</h3>
          <vue-timepicker v-model="end" format="HH:mm"></vue-timepicker>
          </div>
        </div>
        <div class="error" v-if="error"> Fields cannot be empty </div>
        <div class="button-holder">
          <button @click="addEvents" class="button-success">Ok</button>
        </div>
      </template>
    </Modal>
  </div>
</template>

<script>
import moment from 'moment';
import moment_timezone from 'moment-timezone'
import 'moment/locale/ru';
moment.locale('ru');


import TransitionExpand from '@/components/TransitionExpand.vue';
import CustomSelect from '@/components/CustomSelect.vue';
import Modal from '@/components/Modal'
import VueTimepicker from 'vue2-timepicker'
import 'vue2-timepicker/dist/VueTimepicker.css'
export default {
  name: 'Calendar',
  components: {CustomSelect, TransitionExpand,Modal, VueTimepicker},
  data() {
    return {
      error:false,
      start:'',
      end:'',
      description:'',
      moment: moment,
      currentYear: new Date().getFullYear(),
      datePick: '',
      dateNow: new Date().getDate(),
      month: new Date().getMonth(),
      year: new Date().getFullYear(),
      dFirstMonth: '1',
      day: ["Mo", "Tue", "We", "Th", "Fr", "Sa", "Su"],
      task:[{
        start: 1679828400000,
        end: 1679832000000,
        text:'testing message'
      }],
      mapMonth: {
        "0": "January",
        "1": "February",
        "2": "March",
        "3": "April",
        "4": "May",
        "5": "June",
        "6": "July",
        "7": "August",
        "8": "September",
        "9": "October",
        "10": "November",
        "11": "December"
      },
      mapMonthName: {
        "January": "0",
        "February": "1",
        "March": "2",
        "April": "3",
        "May": "4",
        "June": "5",
        "July": "6",
        "August": "7",
        "September": "8",
        "October": "9",
        "November": "10",
        "December": "11"
      },
      date: new Date().getFullYear() + '-' + new Date().getMonth() + '-' + new Date().getDate(),
    }
  },
  computed:{
    eventFilter(){
      let startDayMs = moment(this.datePick).endOf('day').format('x');
      let endDayMs = moment(this.datePick).startOf('day').format('x');

      return this.task.filter(task=> task.start<startDayMs && task.start>endDayMs)
    }
  },
  watch: {
    'datePick': function (now) {
    },

  },
  mounted() {
    this.month = moment(this.valueMs).format("M") - 1
    this.year = Number(moment(this.valueMs).format("YYYY"))
  },
  methods: {
    addEvents(){
      if(this.start!=='' && this.end!=='' && this.description!==''){
        let startMs =  moment(this.datePick+' '+this.start).format('x')
        let endMs = moment(this.datePick+' '+this.end).format('x')
        this.task.push({start:Number(startMs), end:Number(endMs), text: this.description})
        this.$refs.modal_add.close();
      }
      else{
        setTimeout(() => {
          this.error = false
        }, 5000);
        this.error = true;
      }

    },
    openModal(){
      this.start='';
      this.end='';
      this.description='';
      this.$refs.modal_add.open();
    },
    eventDay(now){
      let nowDayStartMs = Number(moment((this.month + 1) + '-' + now + '-' + this.year).startOf('day').format('x'));
      let nowDayEndMs = Number(moment((this.month + 1) + '-' + now + '-' + this.year).endOf('day').format('x'));
      return this.task.some(task=> task.start>nowDayStartMs &&  task.end<nowDayEndMs)
    },
    calendar: function () {
      var days = [];
      var week = 0;
      days[week] = [];
      var dlast = new Date(this.year, this.month + 1, 0).getDate();
      for (let i = 1; i <= dlast; i++) {
        if (new Date(this.year, this.month, i).getDay() != this.dFirstMonth) {
          var a = {index: i};
          days[week].push(a);
        } else {
          week++;
          days[week] = [];
          a = {index: i};
          days[week].push(a);
        }
      }

      if (days[0].length > 0) {
        for (let i = days[0].length; i < 7; i++) {
          days[0].unshift('');

        }
      }
      return days;
    },
    decrease: function () {
      this.month--;
      if (this.month < 0) {
        this.month = 12;
        this.month--;
        this.year--;
      }

    },
    increase: function () {

      this.month++;
      if (this.month > 11) {
        this.month = -1;
        this.month++;
        this.year++;
      }
    },
    nextYear: function () {
      this.year++;

    },
    prevYear: function () {
      this.year--;
    }
  },
}
</script>

<style scoped lang="scss">
.ne-calendar-pick {
  display: flex;
  width: 100%;
  border-bottom: 1px solid #DFE0E1;
  margin-bottom: 10px;
  padding-bottom: 10px;
  justify-content: center;
  align-items: center;
}

.ne-calendar-holder {
  font-family: Muller;
}

.ne-calendar {
  border: 1px solid #E2E2E2;
  padding: 10px;
  background: white;
}

.table {
  width: 100%;
  table-layout: fixed;
}

.table td {
  text-align: center;
}

.ne-calendar-dayWeek-holder {
  font-size: 12px;
  line-height: 20px;
  letter-spacing: 0.1em;
  color: #D1D1D1;
}

.ne-calendar-day:hover {
  background: #e7ebe6;
}

.ne-calendar-day {
  font-style: normal;
  font-size: 12px;
  line-height: 20px;
  letter-spacing: 0.02em;
  padding: 8px;
  color: #323232;
  cursor: pointer;
  border-radius: 8px;
  border-top: 0;
  z-index: 2;

  &.active {
    font-weight: bold;
    background: #cedff3;
    border-radius: 8px;
  }

  &.picked {
    font-weight: bold;
    background: #EBEBEB;
    border-radius: 8px;
  }
  &.disabled {
    pointer-events: none;
  }

  &.event {
    position: relative;
    &:after {
      content: '';
      position: absolute;
      width: 7px;
      height: 7px;
      border-radius: 50%;
      top: 6px;
      right: 6px;
      background: red;
      z-index: -1;

    }
  }


}

.nav-arrow {
  border: 1px solid #E2E2E2;
  padding: 3px;
  margin: 0 10px;
  border-radius: 3px;
}

.icon-arrow {
  position: relative;
  top: -1px;

  &.right {
    transform: rotate(-90deg);
  }

  &.left {
    transform: rotate(90deg);
  }
}

.month-pick {
  min-width: 85px;
  text-align: center;
}
.event-holder{
  border: 1px solid #E2E2E2;
  padding: 10px;
  background: white;
  position: relative;
}

.button {
  display: block;
  position: absolute;
  top: 5px;
  right: 5px;
  width: 40px;
  height: 40px;
  border-radius: 50%;
}
.button > span {
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
}
.bg {
  border-radius: 50%;
  background-color: rgba(224, 52, 52, 0.9);
  box-shadow: 0 2px 3px rgba(0, 0, 0, 0.1);
  transition: all 0.2s linear;
}
.symbol::before, .symbol::after {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  display: block;
  margin: auto;
  border-radius: 2px;
  content: "";
}
.symbol::before{
  width: 15px;
  height: 2px;
  background-color: white;
  transition: background-color 1s linear;
}
.plus .symbol::after {
  width: 2px;
  height: 15px;
  background-color: white;
}
.bg::before, .bg::after {
  position: absolute;
  top: -4.75rem;
  left: -4.75rem;
  display: block;
  width: 15rem;
  height: 15rem;
  border: 4px solid #fff;
  border-radius: 50%;
  box-sizing: border-box;
  content: "";
  transform: scale(0.4);
  opacity: 0;
}
.button:hover .bg {
  background-color: rgb(145, 36, 36)
}
.event-time-holder{
  margin-top: 10px;
}
.event-time{
  display: flex;
}
.event-list{
  border-bottom: 1px solid black;
  h3{
    margin: 0 0 5px 0;
  }
}
.time-holder{
  display: flex;
  justify-content: space-between;
}
.textarea-modal{
  width: 100%;
  resize: none;
}
.button-success{
  background-color: rgba(224, 52, 52, 0.9);
  box-shadow: 0 2px 3px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  transition: all 0.3s;
  padding: 10px 30px;
  color: white;
  stroke: none;
  border: 0;
  cursor: pointer;
  &:hover {
    background-color: rgb(145, 36, 36)
  }
}
.button-holder{
  width: 100%;
  justify-content: flex-end;
  display: flex;
  margin: 20px 0 0 0;
}
.error{
  color: red;
  margin: 10px 0;
}
</style>
