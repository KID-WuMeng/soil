<template lang="jade">

  .circle-sign

</template>



<style lang="less">

  @import "../../asset/style/color.less";

  @out-circle-size: 12px;
  @in-circle-size: 4px;

  .soil-radio{
    .circle-sign{
      display: inline-flex;
      justify-content: center;
      align-items: center;
      width: @out-circle-size;
      height: @out-circle-size;
      color: @soil-blue;
      border: 1px solid @soil-gray-4;
      border-radius: 100%;
      &:after{
        display: inline-block;
        content: "";
        width: @in-circle-size;
        height: @in-circle-size;
        transform: scale3d(0, 0, 1);
        color: inherit;
        background-color: currentColor;
        border-radius: 100%;
        transition: transform 0.3s ease;
      }
    }
  }

  .soil-radio.-active{
    >.circle-sign{
      &:after{
        transform: scale3d(1, 1, 1);
      }
    }
  }

</style>