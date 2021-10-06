<template>
  <div>
    <FullCalendar :options="calendarOptions" />
    <select id="cars" class="dropdown" @change="changeCar">
      <option value="volvo">Volvo</option>
      <option value="saab">Saab</option>
      <option value="vw">VW</option>
      <option value="audi" selected>Audi</option>
    </select>
  </div>
</template>
<script>
import "@fullcalendar/core/vdom"; // solve problem with Vite
import FullCalendar from "@fullcalendar/vue3";
import dayGridPlugin from "@fullcalendar/daygrid";
import timeGridPlugin from "@fullcalendar/timegrid";
import interactionPlugin from "@fullcalendar/interaction";
import resourceTimeGridPlugin from "@fullcalendar/resource-timegrid";

export default {
  components: {
    FullCalendar, // make the <FullCalendar> tag available
  },
  data() {
    return {
      resourceid: {
        a: 0,
        b: 0,
      },
      calendarOptions: {
        plugins: [
          dayGridPlugin,
          timeGridPlugin,
          interactionPlugin,
          resourceTimeGridPlugin,
        ],
        dayMaxEvents: 4,
        // dayMaxEventRows: true,
        // eventLimit: true,
        views: {
          dayGridMonth: {
            titleFormat: { day: "2-digit", month: "short", year: "numeric" },
          },
        },
        initialView: "resourceTimeGridDay",
        resources: [
          { id: "a", title: "Room A" },
          // { id: '2', title: ''},
          // { id: '3', title: '' },
          // { id: '4', title: ''},
          // { id: '5', title: '' },
          { id: "b", title: "Room B" },
          // { id: '7', title: '' },
          // { id: '8', title: ''},
        ],
        dateClick: this.handleDateClick,
        eventClick: this.handleEventClick,
        weekends: true,
        headerToolbar: {
          left: "dayGridMonth,timeGridWeek,resourceTimeGridDay",
          center: "title",
          right: "prev,next",
        },
        // aspectRatio: 5,
        // expandRows: true,
        slotLabelFormat: {
          hour: "numeric",
          minute: "2-digit",
          omitZeroMinute: false,
          meridiem: false,
        },
        dayHeaderFormat: {
          weekday: "short",
          day: "numeric",
        },
        datesAboveResources: true,
        eventMinHeight: 20,
        eventShortHeight: 35,
        contentHeight: "auto",
        // height:'100%',
        slotMinTime: "08:00:00",
        slotMaxTime: "18:00:00",
        eventDisplay: "block",
        slotDuration: "01:00:00",
        slotEventOverlap: false,
        events: [
          {
            resourceId: "a",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T08:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 1,
            },
          },
          {
            resourceId: "a",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T08:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 1,
            },
          },
          {
            resourceId: "a",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T08:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 1,
            },
          },
          {
            resourceId: "a",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T08:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 1,
            },
          },
          {
            resourceId: "b",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T08:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 1,
            },
          },
          {
            resourceId: "b",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T08:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 1,
            },
          },
          {
            resourceId: "b",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T08:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 1,
            },
          },
          {
            resourceId: "b",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T08:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 1,
            },
          },

          //9h
          {
            resourceId: "a",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T09:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 2,
            },
          },
          {
            resourceId: "a",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T09:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 2,
            },
          },
          {
            resourceId: "a",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T09:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 2,
            },
          },
          {
            resourceId: "a",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T09:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 2,
            },
          },
          {
            resourceId: "b",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T09:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 2,
            },
          },
          {
            resourceId: "b",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T09:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 2,
            },
          },
          {
            resourceId: "b",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T09:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 2,
            },
          },
          {
            resourceId: "b",
            id: Math.random(),
            title: "Lien Ho-cloud 1",
            start: "2021-10-06T09:00:00",
            allDay: false,
            backgroundColor: "pink",
            extendedProps: {
              icon: "cloud",
              index: 3,
            },
          },
          // other events here...
        ],
        displayEventTime: false,
        nowIndicator: true,
        now: new Date(),
        businessHours: [
          // specify an array instead
          {
            daysOfWeek: [1, 2, 3, 4, 5], // Monday, Tuesday, Wednesday
            startTime: "08:00", // 8am
            endTime: "11:00", // 6pm
          },
          {
            daysOfWeek: [1, 2, 3, 4, 5], // Thursday, Friday
            startTime: "13:00", // 10am
            endTime: "18:00", // 4pm
          },
        ],
        eventContent: function(info) {
          let italicEl = document.createElement("div");
          italicEl.innerHTML = `<div class ="custom-title"><div>${info.event.title}</div><div class="text-center"><i class="calendar-icon fas fa-plus"></i></span></div></div>`;
          let arrayOfDomNodes = [italicEl];
          return { domNodes: arrayOfDomNodes };
        },
        eventResizableFromStart: true,

        eventDidMount: function(info) {
          console.log(info);
        },
      },
    };
  },
  methods: {
    handleDateClick(arg) {
      console.log(arg);
      this.calendarOptions.events.push({
        resourceId: arg.resource.id,
        title: "",
        start: arg.dateStr,
      });
    },
    handleEventClick(arg) {
      const index = this.calendarOptions.events.findIndex(
        (x) => +x.id === +arg.event.id
      );
      let endTime= "2021-10-06T10:00:00"
      this.calendarOptions.events[index].backgroundColor = "blue";
      this.calendarOptions.events[index].end = endTime;
       let endTimeNumber =this.getHour(endTime)
       let start 
      // const index2 = this.calendarOptions.events.findIndex(
      //   (x) =>
      //     {
      //      console.log( x.end?.split("T")[1].split(":")[0] -1 ,arg.event.start.getHours(), x.resourceId , arg.event._def.resourceIds[0]) 
      //       return x.extendedProps.index == arg.event.extendedProps.index &&
      //     x.end?.split("T")[1].split(":")[0] -1 === arg.event.start.getHours() &&
      //     x.resourceId == arg.event._def.resourceIds[0]}
      // );
      this.calendarOptions.events.splice(index2, 1);
      console.log(2, arg, index2);
    },
    changeCar(event) {
      console.log(2, event);
    },
    getHour(number) {
     return number?.split('T')[1].split(':')[0]
    }
  },
};
</script>

<style>
.fc {
  position: relative;
}
.dropdown {
  position: absolute;
  top: 20px;
  right: 160px;
  z-index: 2;
}
.fc-button-group.fc-button.fc-button-primary.fc-button-active {
  background: #1e5199;
  color: #fff;
}
.fc-button-group.fc-button {
  background: #fff;
  color: #1e5199;
}

.custom-text {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 10px;
}

.custom-title {
  display: flex;
  justify-content: space-between;
}

.fc-scrollgrid-section-body tr {
  height: 130px;
}

.fc-scrollgrid-section-body:nth-child(1) tr {
  height: 100px;
}

td.fc-daygrid-day.fc-day.fc-day-tue.fc-day-today {
  background: white;
}
td.fc-daygrid-day.fc-day.fc-day-tue.fc-day-today a.fc-daygrid-day-number {
  border: 1px solid black;
  width: 25px;
  height: 25px;
  background-color: pink;
  border-radius: 50%;
  display: flex;
  justify-content: center;
}

.fc-timegrid-event-harness.fc-timegrid-event-harness-inset:last-child {
  margin-right: 0;
}
.fc .fc-daygrid-body-natural .fc-daygrid-day-events {
  margin-bottom: 1em;
  display: flex;
  gap: 1em;
}
/* .fc-event{
  width: 98px !important;} */
</style>
