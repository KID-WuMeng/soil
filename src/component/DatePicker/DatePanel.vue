<template lang="jade">

  .date-panel
    date-panel-head(
      :month-labels="monthLabels",
      :year="year",
      :month="month",
      @prev-year="$emit('prev-year')",
      @next-year="$emit('next-year')",
      @prev-month="$emit('prev-month')",
      @next-month="$emit('next-month')",
      @switch-year-panel="$emit('switch-year-panel')",
      @switch-month-panel="$emit('switch-month-panel')"
    )
    date-panel-body(
      :day-labels="dayLabels",
      :year="year",
      :month="month",
      @pick="onPick"
    )

</template>



<script lang="coffee">

  module.exports =

    components:
      'date-panel-head': require './DatePanelHead'
      'date-panel-body': require './DatePanelBody'

    props:
      'monthLabels':
        type: Array
        required: true
      'dayLabels':
        type: Array
        required: true
      'year':
        type: Number
        required: true
      'month':
        type: Number
        required: true

    methods:
      'onPick': (date) -> @$emit('pick', date)

</script>



<style lang="less">

  @import "../../asset/style/color.less";

  .soil-date-picker{
    .date-panel-head{
      margin-top: 12px;
    }
    .date-panel-body{
      margin-top: 16px;
    }
  }

</style>