<template>
  <div>
    <div class="dialog-wrap">
      <transition name="fade">
        <div class="dialog-cover" v-if="isShow" @click="closeMyself"></div>
      </transition>
      <transition name="drop">
        <div class="dialog-content" v-if="isShow">
          <p class="dialog-close" @click="closeMyself">×</p>
          <slot>empty</slot>
        </div>
      </transition>
    </div>
  </div>
</template>
<script type="text/javascript">
  export default {
    props: {
      isShow: {
        type: Boolean,
        default: false
      }
    },
    data () {
      return {
        a: 1
      }
    },
    methods: {
      closeMyself () {
        this.$emit('on-close')
      }
    }
  }
</script>
<style type="text/css" scoped>
  .fade-enter-active {
    transition: all .5s ease-out;
  }
  .fade-enter {
    opacity: 0;
  }
  .fade-leave-active {
    transition: all .3s ease-out;
    opacity: 0;
  }
  .drop-enter-active {
    transition: all .5s ease;
  }
  .drop-enter {
    transform: translateY(-500px);
  }
  .drop-leave-active {
    transition: all .3s ease;
    transform: translateY(-500px);
  }

  .dialog-wrap {
    position: fixed;
    width: 100%;
    height: 100%;
  }
  .dialog-cover {
    background: rgba(0, 0, 0, 0.3);
    position: fixed;
    z-index: 5;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
  .dialog-content {
    width: 50%;
    position: fixed;
    max-height: 50%;
    overflow: auto;
    background: #fff;
    top: 20%;
    left: 50%;
    margin-left: -25%;
    z-index: 10;
    border: 2px solid #464068;
    padding: 2%;
    line-height: 1.6;
  }
  .dialog-close {
    position: absolute;
    right: 5px;
    top: 5px;
    width: 20px;
    height: 20px;
    text-align: center;
    cursor: pointer;
  }
  .dialog-close:hover {
    color: #4fc08d;
  }
</style>