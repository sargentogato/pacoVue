<template>
  <button class="menu-item" @click="isOpen = !isOpen">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      version="1.1"
      id="Capa_1"
      x="0px"
      y="0px"
      width="20px"
      height="20px"
      viewBox="0 0 960 560"
      enable-background="new 0 0 960 560"
      xml:space="preserve"
    >
      <path
        d="M480,344.181L268.869,131.889c-15.756-15.859-41.3-15.859-57.054,0c-15.754,15.857-15.754,41.57,0,57.431l237.632,238.937   c8.395,8.451,19.562,12.254,30.553,11.698c10.993,0.556,22.159-3.247,30.555-11.698l237.631-238.937   c15.756-15.86,15.756-41.571,0-57.431s-41.299-15.859-57.051,0L480,344.181z"
      />
    </svg>
    <transition name="fade" appear>
      <div class="sub-menu" v-if="isOpen">
        <a class="itemLink myAcount" href=""
          ><span>
            <svg
              xmlns:svg="http://www.w3.org/2000/svg"
              xmlns="http://www.w3.org/2000/svg"
              version="1.1"
              id="Capa_1"
              x="0px"
              y="0px"
              width="20px"
              height="20px"
              viewBox="0 0 512.002 512.002"
              enable-background="new 0 0 960 560"
              xml:space="preserve"
            >
              <path
                d="M 388.425,241.951 151.609,5.79 c -7.759,-7.733 -20.321,-7.72 -28.067,0.04 -7.74,7.759 -7.72,20.328 0.04,28.067 l 222.72,222.105 -222.728,222.104 c -7.759,7.74 -7.779,20.301 -0.04,28.061 3.883,3.89 8.97,5.835 14.057,5.835 5.074,0 10.141,-1.932 14.017,-5.795 L 388.425,270.052 c 3.737,-3.718 5.834,-8.778 5.834,-14.05 0,-5.272 -2.103,-10.326 -5.834,-14.051 z"
                id="path2"
                inkscape:connector-curvature="0"
              />
            </svg>
          </span>
          Mis Cuentas</a
        >
        <div v-for="worker of users" :key="worker" class="toolTip">
          <h3>{{ worker }}</h3>
          <p>
            Hoy llevas: {{ time.hours }}:{{ time.minutes }}:{{ time.seconds }}
          </p>
        </div>
        <div v-for="(item, i) in itemsMenu" :key="i" class="menu-item">
          <a class="itemLink" href="#">{{ item.title }}</a>
        </div>
      </div>
    </transition>
  </button>
</template>

<script>
export default {
  name: "dropdown",
  props: ["itemsMenu", "time", "users"],
  data() {
    return {
      isOpen: false,
    };
  },
};
</script>

<style>
.menu-item {
  position: relative;
  text-align: center;
}

.itemLink {
  padding: 20px 20px;
  display: block;
  width: 100%;
  border-bottom: 1px solid hsl(0, 0%, 85%);
  color: rgb(0, 0, 0);
}

.sub-menu *:last-child *:last-child {
  border-bottom: unset;
}

.sub-menu {
  box-shadow: 0px 1px 10px 1px rgba(150, 150, 150, 1);
}

.sub-menu {
  position: absolute;
  background-color: rgb(255, 255, 255);
  border-radius: 15px;
  top: calc(100% + 18px);
  transform: translateX(-100%);
  width: 25rem;
  text-align: center;
}

.fade-enter-active,
.fade-leaver-active {
  transition: 0.5s ease-in-out;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.toolTip {
  display: none;
}

.myAcount:hover + .toolTip {
  display: block;
  position: absolute;
  background-color: inherit;
  box-shadow: inherit;
  border-radius: inherit;
  top: 0;
  width: 25rem;
  padding: 0.5rem 0;
  transform: translateX(-101%);
}

.myAcount:hover,
.itemLink:hover {
  color: rgb(86, 192, 0);
}

span {
  position: absolute;
  right: 1rem;
  left: 0.5rem;
}

span > svg {
  transform: rotate(180deg);
}
</style>
