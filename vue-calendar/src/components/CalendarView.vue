<script>
import FullCalendar from "@fullcalendar/vue3";
import multiMonthPlugin from "@fullcalendar/multimonth";
import interactionPlugin from "@fullcalendar/interaction";
import jaLocale from "@fullcalendar/core/locales/ja"; // 日本語化用
import holidayJp from "@holiday-jp/holiday_jp";

export default {
  components: {
    FullCalendar,
  },
  data() {
    return {
      calendarOptions: {
        // カレンダーで使用するプラグイン
        plugins: [multiMonthPlugin, interactionPlugin],
        initialView: "multiMonthYear",
        // 土日を表示
        weekends: true,
        events: this.getEvents(),
        locale: jaLocale,
        // 日付セルのカスタムクラスを設定
        dayCellClassNames: this.dayCellClassNames,
        // 数字のみの日付
        dayCellContent: function (e) {
          return e.dayNumberText.replace("日", "");
        },
      },
    };
  },
  methods: {
    getEvents() {
      const currentYear = new Date().getFullYear();
      const holidays = holidayJp.between(
        new Date(`${currentYear}-01-01`),
        new Date(`${currentYear}-12-31`)
      );

      return holidays.map((holiday) => ({
        title: holiday.name,
        // タイムスタンプをDateオブジェクトに変換する
        start: new Date(holiday.date),
        allDay: true,
      }));
    },
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

<template>
  <FullCalendar :options="calendarOptions" :locale="locale" />
</template>

<style>
.blue {
  background-color: lightskyblue;
}

.red {
  background-color: lightcoral;
}
</style>
