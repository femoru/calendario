<template>
  <v-sheet>
    <v-container>
      <calendar-header v-model="month" />
      <calendar-body v-model="month" v-bind="$attrs" v-on="$listeners" />
    </v-container>
  </v-sheet>
</template>
<script>
import CalendarHeader from "./CalendarHeader.vue";
import CalendarBody from "./CalendarBody.vue";
export default {
  components: {
    CalendarHeader,
    CalendarBody,
  },
  props: {
    value: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      month: new Date().toISOString().substr(0, 7),
    };
  },
  created() {
    this.month = this.value;
  },
  watch: {
    value: {
      deep: true,
      handler(newValue) {
        this.month = newValue;
      },
    },
  },
};
</script>
<style lang="scss" >
.calendar-cell {
  min-width: calc(100% / 7);
}
.calendar-body > .row > .calendar-cell {
  border: 0.001rem dotted #81BEBE !important;
}
</style>