<template lang="jade">

  .shadow-layer(:style="styleObject")

</template>



<script lang="coffee">

  module.exports =

    props:
      'alpha':
        type: Number
        required: true

    computed:
      'styleObject': ->
        'backgroundColor': "rgba(0, 0, 0, #{@alpha})"

</script>



<style lang="less">

  @import "../../asset/style/color.less";

  .shadow-layer {
    width: 100%;
    height: 100%;
    transition: background-color 0.3s ease;
  }

  .-drawing > .shadow-layer { transition: none }

</style>