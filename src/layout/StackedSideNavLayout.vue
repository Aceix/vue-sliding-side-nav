<template>
  <div class="stacked-side-nav-layout">
    <button id="menu-btn" @click="toggleMenu">MENU</button>

    <nav id="menu" :class="[isMenuOpen ? 'maximised' : 'minimised']">
      <!-- <transition-group> -->
      <div id="menu-content">
        <div>Hello1</div>
        <div>Hello2</div>
        <div>Hello3</div>
        <div>Hello4</div>
      </div>
      <!-- </transition-group> -->
    </nav>
    <main id="main" :class="[isMenuOpen ? 'minimised' : '']">
      <HelloWorld />
    </main>
  </div>
</template>

<script>
import HelloWorld from "../components/HelloWorld";

export default {
  name: "stacked-side-nav-layout",
  components: { HelloWorld },
  data() {
    return {
      isMenuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
  },
};
</script>

<style scoped>
.stacked-side-nav-layout {
  width: 100vw;
  height: 100vh;
  position: relative;
  overflow: hidden;
  display: flex;
  background: yellowgreen;
}
#menu-btn {
  position: absolute;
  top: 25px;
  left: 25px;
  z-index: 10;
}
#menu {
  flex: 1 0 auto;
  width: 0%;
  height: 100%;
  transition: 400ms all;
}
#menu.maximised {
  width: 80%;
}
#menu-content {
  width: 80%;
  background: green;
  opacity: 0;
  /* transition: 200ms all; */
}
#menu.maximised > #menu-content {
  animation: slide-in-bottom 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
  animation-delay: 400ms;
}
#menu.minimised > #menu-content {
  animation: slide-out-left 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
}

#main {
  flex: 1 0 auto;
  background: yellow;
  width: 100%;
  height: 100%;
  transition: 400ms all;
  overflow: auto;
}
#main.minimised {
  width: 20%;
  height: 90%;
  align-self: center;
}

@keyframes slide-in-bottom {
  0% {
    transform: translateY(50px);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}
@keyframes slide-out-left {
  0% {
    transform: translateY(0px);
    opacity: 1;
  }
  100% {
    transform: translateX(-50px);
    opacity: 0;
  }
}
</style>
