<script>
import { useStore } from 'vuex'
export default {
  setup() {
    // useStore 提供store操作內容
    const store = useStore()
    // 單一return isOpen，而不是將整個store丟出
    const isOpen = computed(()=>{
      return store.getters.isOpen
    })

    const handClickMenu = () => {
      console.log(isOpen)
    };
    // 要呈現在HTML上的
    return { handClickMenu,isOpen };
  },
};
</script>

<template>
  <div :class="['menu',{ open:store.state.isOpen}]">
    <a class="closeBtn" @click="handClickMenu">
      <i class="fas fa-times fa-3x"></i>
    </a>
    <ul class="nav">
      <li><a>abous</a></li>
      <li><a>content</a></li>
      <li><a>user</a></li>
      <li><a>address</a></li>
    </ul>
  </div>
</template>
<style lang="scss" scoped>
.menu {
  position: fixed;
  top: 0;
  right: -350px;
  width: 350px;
  height: 100%;
  z-index: 20;
  background-color: #fff;
  transition: right 0.3s;
  &.open {
    right: 0px;
  }
  > a.closeBtn {
    cursor: pointer;
    position: absolute;
    right: 50px;
    top: 50px;
  }
  > ul.nav {
    position: absolute;
    width: 100%;
    height: 300px;
    top: 50%;
    margin-top: -150px;
    padding: 0;
    > li {
      display: block;
      width: 100%;
      height: 25%;
      > a {
        cursor: pointer;
        display: block;
        width: 100%;
        height: 100%;
        padding-left: 50px;
        line-height: 300%;
        font-size: 22px;
      }
    }
  }
}
</style>
