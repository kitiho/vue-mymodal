<template>
  <transition>
    <div class="my-modal">
      <div class="mask"></div>
      <div class="wrapper">
        <div class="wrapper-header">{{ title }}</div>
        <div class="wrapper-body">
          <slot name="modalMessage" :data="`111`"></slot>
        </div>
        <div class="wrapper-footer">
          <button @click="closeModal" class="btn btn-skip">SKIP</button>
          <button @click="go" class="btn btn-next">NEXT</button>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default() {
        return "Hold on!";
      },
      validator(v) {
        return v !== "";
      }
    }
  },
  methods: {
    closeModal() {
      this.$emit("closeModal");
    },
    go() {
      this.$emit("go");
    }
  }
};
</script>

<style lang="scss" scoped>
* {
  box-sizing: border-box;
}
button {
  margin: 0;
  padding: 0;
  border: none;
  outline: none;
}
.v-enter-active {
  transition: all 0.3s ease;
}
.v-leave-active {
  transition: all 0.3s ease;
}
.v-enter, .v-leave-to
/* .slide-fade-leave-active for below version 2.1.8 */ {
  transform: translateY(-10px);
  opacity: 0;
}
.my-modal {
  font-family: "Verdana";
  width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  left: 0;
  .mask {
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;
    background: #000;
    opacity: 0.5;
    z-index: -99;
  }
  .wrapper {
    background: #fffbff;
    width: 20rem;
    height: auto;
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translate(-50%, -50%);
    border-radius: 0 4rem 0 4rem;
    padding: 1.3rem 2rem;
    .wrapper-header {
      font-weight: bold;
      font-size: 1.8rem;
      padding-bottom: 0.5rem;
    }
    .wrapper-body {
      color: #b7b1ba;
      font-size: 0.8rem;
      padding: 0.5rem 0;
      padding-bottom: 2rem;
    }
    .wrapper-footer {
      text-align: right;
      .btn {
        cursor: pointer;
        width: 4.5rem;
        height: 2.5rem;
        background: #8b56ac;
        border-radius: 2rem;
        font-size: 0.9rem;
        color: #fffbff;
        margin: 0 0 0 0.6rem;
        &.btn-skip {
          background: #b6b9d0;
        }
      }
    }
  }
}
</style>