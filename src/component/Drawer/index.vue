<template lang="jade">

  .soil-drawer(:class="rootClassObject", :style="rootStyleObject")

    .mask(
      :style="maskStyleObject",
      @click.self="onClickShadow"
    )
      component(
        ref="panel",
        :is="panelType",
        :hide-on-draw="hideOnDraw",
        :hide-on-swipe="hideOnSwipe",
        @ready="onReadyPanel",
        @draw-start="onDrawStart",
        @draw="onDraw"
        @draw-end="onDrawEnd",
        @swipe-end="onSwipeEnd",
        @show-start="onShowStart",
        @hide-start="onHideStart",
        @hide-end="onHideEnd",
      )
        slot

</template>



<script lang="coffee">

  module.exports =

    components:
      'left-panel': require './LeftPanel'
      'right-panel': require './RightPanel'
      'top-panel': require './TopPanel'
      'bottom-panel': require './BottomPanel'


    props:

      'from':
        type: String
        default: 'left'

      'shadow':
        type: Boolean
        default: true

      'alpha':
        type: Number
        default: 0.6

      'hideOnDraw':
        type: Boolean
        default: true

      'hideOnSwipe':
        type: Boolean
        default: true

      'hideOnClickShadow':
        type: Boolean
        default: true


    data: ->
      'open': false
      'width': null
      'dynamicAlpha': @alpha
      'drawing': @drawing


    computed:

      'panelType': -> "#{@from}-panel"

      'rootClassObject': ->
        '-shadow': @shadow
        '-drawing': @drawing

      'rootStyleObject': ->
        'visibility': if @open then 'visible' else 'hidden'

      'maskStyleObject': ->
        'backgroundColor': "rgba(0, 0, 0, #{@dynamicAlpha})"



    methods:

      'show': ->
        @open = true
        this.$refs.panel.show()

      'hide': ->
        this.$refs.panel.hide()

      'onReadyPanel': (width) ->
        @width = width

      'onDrawStart': ->
        @drawing = true

      'onDrawEnd': ->
        @drawing = false

      'onSwipeEnd': ->
        @drawing = false

      'onShowStart': ->
        @dynamicAlpha = @alpha

      'onHideStart': ->
        @dynamicAlpha = 0

      'onHideEnd': ->
        @open = false

      'onDraw': (distance) ->
        ratio = 1 - distance / @width
        @dynamicAlpha = @alpha * ratio

      'onClickShadow': ->
        if @hideOnClickShadow then @hide()

</script>



<style lang="less">

  @import "../../asset/style/color.less";

  .soil-drawer {
    position: fixed;
    left: 0;
    top: 0;
    z-index: 100;
    width: 100%;
    height: 100%;

    .mask {
      width: 100%;
      height: 100%;
      transition: background-color 0.3s ease;

      // @REVIEW
      // Fix the bug in the Safari ( macOS and iOS ),
      // which can't display mask in the second time.
      // I haven't found the reason yet.
      // I'm not sure if it is related to the transition of mask
      // or transform ( translate3d ) of panel.
      transform: translate3d(0, 0, 1px);

      .panel {
        position: absolute;
        display: inline-block;
        transition: transform 0.3s ease;
      }
    }
  }


  .soil-drawer.-drawing {
    .mask {
      transition: none;
      .panel { transition: none }
    }
  }


  .soil-drawer.-shadow {
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  }

</style>