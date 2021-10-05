<template>
  <div>
    <FullCalendar :options="calendarOptions"  />
    <select id="cars" class="dropdown" @change="changeCar">
      <option value="volvo">Volvo</option>
      <option value="saab">Saab</option>
      <option value="vw">VW</option>
      <option value="audi" selected>Audi</option>
    </select>
  </div>
</template>
<script>
import '@fullcalendar/core/vdom' // solve problem with Vite
import FullCalendar from '@fullcalendar/vue3'
import dayGridPlugin from '@fullcalendar/daygrid'
import timeGridPlugin from '@fullcalendar/timegrid'
import interactionPlugin from '@fullcalendar/interaction'
import resourceTimeGridPlugin from '@fullcalendar/resource-timegrid';

export default {
  components: {
    FullCalendar, // make the <FullCalendar> tag available
  },
  data() {
    return {
      calendarOptions: {
        plugins: [dayGridPlugin, timeGridPlugin, interactionPlugin,resourceTimeGridPlugin],
        dayMaxEvents:4,
        // dayMaxEventRows: true,
          // eventLimit: true,
        views: {
          dayGridMonth: {
            titleFormat: { day: '2-digit', month: 'short', year: 'numeric' },
          },
          
        },
        initialView: 'resourceTimeGridDay',
    resources: [
      { id: 'a', title: 'Room A' },
      { id: 'b', title: 'Room B'},
    ],
        dateClick: this.handleDateClick,
        eventClick: this.handleEventClick,
        weekends: true,
        headerToolbar: {
          left: 'dayGridMonth,timeGridWeek,resourceTimeGridDay',
          center: 'title',
          right: 'prev,next',
        },
        // aspectRatio: 5,
        // expandRows: true,
        slotLabelFormat: {
          hour: 'numeric',
          minute: '2-digit',
          omitZeroMinute: false,
          meridiem: false,
        },
        dayHeaderFormat: {
          weekday: 'short',
          day: 'numeric',
        },
        datesAboveResources:true,
        eventMinHeight:20,
        eventShortHeight:35,
         contentHeight:'auto',
        // height:'100%',
        slotMinTime:'08:00:00',
        slotMaxTime:'18:00:00',
        eventDisplay: 'block',
        slotDuration:'01:00:00', 
        slotEventOverlap:false,
        events: [
          {
            resourceId:'a',
            id:'1',
            title: 'Lien Ho-cloud 1',
            start: '2021-09-29T14:00:00',
            end: '2021-09-29T16:15:00',
            allDay: false,
            backgroundColor: 'pink',
            extendedProps:{
              icon :'cloud'
            }
          },
          {
            title: 'Lien Ho-cloud 2',
            start: '2021-09-29T14:15:00',
            end: '2021-09-29T16:30:00',
            allDay: false,
            backgroundColor: 'pink',
            extendedProps:{
              icon :'cloud'
            }
          },
          {
            title: 'Lien Ho-cloud 3',
            start: '2021-09-29T14:30:00',
            end: '2021-09-29T14:45:00',
            allDay: false,
            backgroundColor: 'pink',
            extendedProps:{
              icon :'cloud'
            }
          },
          {
            title: 'Lien Ho-cloud 4',
            start: '2021-09-29T14:45:00',
            end: '2021-09-29T15:00:00',
            allDay: false,
            backgroundColor: 'pink',
            extendedProps:{
              icon :'cloud'
            }
          },
         {
            title: 'Lien Ho-cloud 5',
            start: '2021-09-29T15:00:00',
            end: '2021-09-29T15:15:00',
            allDay: false,
            backgroundColor: 'pink',
            extendedProps:{
              icon :'cloud'
            }
          },
          {
            title: 'Lien Ho-cloud 6',
            start: '2021-09-29T15:15:00',
            end: '2021-09-29T15:30:00',
            allDay: false,
            backgroundColor: 'blue',
            extendedProps:{
              icon :'cloud'
            }
          },

          // other events here...
        ],
        displayEventTime:false,
        nowIndicator: true,
        now: new Date() ,
        businessHours: [ // specify an array instead
            {
              daysOfWeek: [ 1, 2, 3,4,5 ], // Monday, Tuesday, Wednesday
              startTime: '08:00', // 8am
              endTime: '12:00' // 6pm
            },
            {
              daysOfWeek: [ 1,2,3,4,5 ], // Thursday, Friday
              startTime: '13:00', // 10am
              endTime: '18:00' // 4pm
            }
          ],
      
        eventContent: function(info) {
          console.log(info)
             let italicEl = document.createElement('div')
             italicEl.innerHTML =   `<div class ="custom-title"><div>${info.event.title}</div><div class="text-center"><i class="calendar-icon fas fa-plus"></i></span></div></div>`
            let arrayOfDomNodes = [ italicEl ]
            return { domNodes: arrayOfDomNodes }
        },
        
        
 eventDidMount: function(info) {
  if (info.view.type === 'listDay') {
    var toInject = [];
    toInject.push('test column 1');
    toInject.push('test column 2');
    for (var i = 0; i < toInject.length; i++) {
      var columnElement = document.createElement('td');
      columnElement.textContent = toInject[i];
      info.el.append(columnElement);
    }
  }
},
// viewDidMount: function(arg) {
//   if (arg.view.type === 'listDay') {
//     var tableHeader = $(".fc-list-table th");
//     var listEvents = $('tr.fc-list-event');
//     var maxCol = 0;
//     var arrayLength = listEvents.length;
//     for (var i = 0; i < arrayLength; i++) {
//       maxCol = Math.max(maxCol, listEvents[i].children.length);
//     }
//     tableHeader.attr("colspan", maxCol);
//   }
// },
    }
  }
  },
  methods: {
    handleDateClick(arg) {
      console.log(1, arg)
    },
    handleEventClick(arg) {
      console.log(2, arg)
    },
    changeCar (event) {
      console.log(this.calendarOptions, event.target.value)
      this.calendarOptions.events.push({
      resourceId: 'a',
      title: 'my event',
      start: new Date()
      
    })

    }
  },
}
</script>

<style>
.fc{
  position: relative;
}
.dropdown{
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

.custom-text{
  display:flex;
  justify-content:space-between;
  align-items: center;
}

.custom-title {
  display:flex;
  justify-content:space-between;
  margin-top:5px
}

.fc-scrollgrid-section-body   tr{
  height: 130px;
 }

 .fc-scrollgrid-section-body:nth-child(1)   tr{
  height: 100px;
 }
</style>
