<script>
import FullCalendar from "@fullcalendar/vue3";
import multiMonthPlugin from "@fullcalendar/multimonth";
import interactionPlugin from "@fullcalendar/interaction";
import jaLocale from "@fullcalendar/core/locales/ja";
import googleCalendarPlugin from "@fullcalendar/google-calendar";

export default {
  components: {
    FullCalendar,
  },
  data() {
    return {
      calendarOptions: {
        plugins: [multiMonthPlugin, interactionPlugin, googleCalendarPlugin],
        googleCalendarApiKey: "googleCalendarApiKey",
        events: {
          googleCalendarId: "japanese__ja@holiday.calendar.google.com", // 日本の祝日カレンダー
        },
        initialView: "multiMonthYear",
        // 土日を表示
        weekends: true,
        locale: jaLocale,
        // 日付セルのカスタムクラスを設定
        dayCellClassNames: this.dayCellClassNames,
        // 数字のみの日付
        dayCellContent: function (e) {
          return e.dayNumberText.replace("日", "");
        },
        eventRender: this.eventRender, // イベントレンダリングのコールバック関数
      },
    };
  },
  methods: {
    dayCellClassNames(arg) {
      const dayNumber = arg.date.getDay();
      if (dayNumber === 6) {
        // 土曜日のセルにblueクラスを追加
        return "blue";
      }
      if (dayNumber === 0) {
        // 日曜日のセルにredクラスを追加
        return "red";
      }
      return "";
    },
  },
};
</script>

<style>
.blue {
  background-color: lightskyblue;
}

.red {
  background-color: lightcoral;
}
</style>

<template>
  <FullCalendar :options="calendarOptions" :locale="locale" />
</template>
