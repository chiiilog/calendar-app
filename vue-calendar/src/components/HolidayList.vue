<script>
export default {
  data() {
    return {
      holidays: [],
      nowDate: new Date(), // 現在の年月を取得するためのプロパティを追加
    };
  },
  mounted() {
    this.getHolidays(); // getHolidaysメソッドの呼び出し
  },
  methods: {
    getHolidays() {
      const holidayJp = require("@holiday-jp/holiday_jp");
      // between以降に期間の開始日と終了日を指定する
      const nowDate = new Date();
      this.holidays = holidayJp.between(
        new Date(nowDate.getFullYear(), nowDate.getMonth(), 1),
        new Date(nowDate.getFullYear(), nowDate.getMonth() + 1, 0)
      );
      console.log(this.holidays);
    },
  },
};
</script>

<template>
  <div>
    <p>{{ nowDate.getFullYear() }}年{{ nowDate.getMonth() + 1 }}月の祝日は？</p>
    <ul v-if="holidays.length > 0">
      <li
        v-for="holiday in holidays"
        :key="holiday.name"
        style="list-style: none"
      >
        {{ holiday.name }}
      </li>
    </ul>
    <p v-else>なし</p>
  </div>
</template>
