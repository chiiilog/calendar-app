<script>
import FullCalendar from "@fullcalendar/vue3";
import multiMonthPlugin from "@fullcalendar/multimonth";
import interactionPlugin from "@fullcalendar/interaction";
import jaLocale from "@fullcalendar/core/locales/ja"; // 日本語化用

export default {
  components: {
    FullCalendar, // make the <FullCalendar> tag available
  },
  data: function () {
    return {
      calendarOptions: {
        // カレンダーで使用するプラグイン
        plugins: [multiMonthPlugin, interactionPlugin],
        initialView: "multiMonthYear",
        // 土日を表示
        weekends: true,
        events: [{ title: "Meeting", start: new Date() }],
        locale: jaLocale,

        // 数字のみの日付
        dayCellContent: function (e) {
          return e.dayNumberText.replace("日", "");
        },
      },
    };
  },
};
</script>

<template>
  <FullCalendar :options="calendarOptions" :locale="locale" />
</template>
