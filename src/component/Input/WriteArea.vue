<template lang="jade">

  input.write-area(
    :value="value",
    @input="onInput",
    @keydown="onKeyDown"
  )

</template>



<script lang="coffee">

  module.exports =

    props:
      'value':
        type: String
        default: ''

    methods:
      'onInput': (event) ->
        @$emit('input', event.target.value)
      'onKeyDown': (event) ->
        if event.keyCode is 13
          @$emit('key-enter')
</script>



<style lang="less">

  @import "../../asset/style/color.less";

  .soil-input{
    >.write-area{
      height: 28px;
      line-height: 28px;
      font-size: 12px;
      overflow: hidden;
      background-color: transparent;
      border: none;
      -webkit-font-smoothing: subpixel-antialiased;
    }
  }

  .soil-input.-border{
    >.write-area{color: @soil-black-light}
    >.write-area::placeholder{color: @soil-gray-5}
  }
  .soil-input.-underscore{
    >.write-area{color: @soil-black-light}
    >.write-area::placeholder{color: @soil-gray-4}
  }
  .soil-input.-light{
    >.write-area{color: @soil-black-light}
    >.write-area::placeholder{color: @soil-gray-4}
  }
  .soil-input.-dark{
    >.write-area{color: @soil-black-light}
    >.write-area::placeholder{color: @soil-gray-5}
  }
  .soil-input.-disabled{
    >.write-area{color: @soil-gray-4; cursor: not-allowed}
    >.write-area::placeholder{color: @soil-gray-2}
  }

</style>