<template lang="jade">

  .playground
    soil-date-picker
    soil-bar-x

</template>



<script lang="coffee">

  Soil = require './Soil'

  module.exports =

    components: helper.formatComponentTable('aa-bb', 'soil-*')

    data: ->
      comment: ''

    methods:
      'mixCount': (char) ->
        code = char.charCodeAt 0
        return if code <= 255 then 1 else 2
      'onClick': ->
        helper.message '哈哈哈123', -> console.log 111222

</script>



<style lang="less">

  @import "./asset/style/color";

  .d1 {
    width: 48px;
    height: 48px;
    background-color: red;
  }
  .d2 {
    width: 48px;
    height: 48px;
    background-color: blue;
  }
  .d3 {
    width: 48px;
    height: 48px;
    background-color: green;
  }
  .sep1 {
    width: 10px;
    height: 40px;
    background-color: #333;
  }
  .sep2 {
    width: 10px;
    height: 40px;
    background-color: #333;
  }

  body{
    background-color: #f2f2f2;
  }
  .playground{
    padding: 100px;
  }

  .soil-icon{
    color: @soil-gray-8;
  }
  .search{
    font-size: 24px;
  }
  .no{
    font-size: 12px;
  }

  .soil-date-picker{
  }
  .soil-input{
    margin-bottom: 16px;
  }

</style>