<template lang="jade">

  .month-panel-head
    year-range-control(
      :year="year",
      @prev-year="$emit('prev-year')",
      @next-year="$emit('next-year')",
      @switch-year-panel="$emit('switch-year-panel')"
    )

</template>



<script lang="coffee">

  module.exports =

    components:
      'year-range-control': require './YearRangeControl'

    props:
      'year':
        type: Number
        required: true

</script>



<style lang="less">

  @import "../../asset/style/color.less";

  .soil-date-picker{
    .month-panel-head{
      display: flex;
      justify-content: center;
    }
  }

</style>