<template>
  <div class="mainTimeBox flex justify-center mt-8 w-4/5 pt-4 pb-4 bg-gray-200">
    <div class="timeBox flex justify-between items-center pax-4">
      <div class="timeBox__timeBtn flex justify-between items-center p-4">
        <div class="timeBox__timeBtn-currentTime">
          {{ this.displayHours }}:{{ this.displayMinutes }}:{{
            this.displaySeconds
          }}
        </div>
        <button
          @click="
            isActive();
            startTimer();
          "
          v-show="this.active"
          class="timeBox__timeBtn-getIn focus:outline-none text-sm py-2 rounded-full border border-green-600 hover:text-gray-900 hover:bg-green-50"
        >
          Entrar
        </button>
        <button
          @click="pauseTimer()"
          v-show="this.inactive"
          class="timeBox__timeBtn-getIn focus:outline-none text-sm py-2 rounded-full border border-green-600 hover:text-gray-900 hover:bg-green-50"
        >
          Pausa
        </button>
        <button
          @click="isActive(), finishTimer()"
          v-show="this.inactive"
          class="timeBox__timeBtn-getIn focus:outline-none text-sm py-2 rounded-full border border-green-600 hover:text-gray-900 hover:bg-green-50"
        >
          Salir
        </button>
      </div>

      <div class="timeBox__profile flex justify-between items-center p-4">
        <div class="timeBox__profile-img">
          <img src="../assets/profile.png" alt="" />
        </div>
        <h2 class="timeBox__profile-name">Marlon Velásquez</h2>
        <nav>
          <drop-down
            :itemsMenu="services"
            :time="currentTime"
            :users="workers"
          />
        </nav>
      </div>
    </div>
  </div>
</template>

<script>
import dropDown from "./dropDown.vue";
export default {
  name: "userTimeTracker",
  components: { dropDown },
  data() {
    return {
      active: true,
      inactive: false,
      displayHours: 0,
      displayMinutes: 0,
      displaySeconds: 0,
      counter: 0,
      stop: false,
      pauseClicks: 0,
      services: [
        { title: "Vista Empleados", link: "#" },
        { title: "Mi perfil", link: "#" },
        { title: "Cerrar sesión", link: "#" },
      ],
      workers: ["Marlon"],
    };
  },
  methods: {
    isActive() {
      this.active = !this.active;
      this.inactive = !this.inactive;
    },
    startTimer() {
      this.counter = setInterval(() => {
        if (this.displaySeconds === 60) {
          this.displaySeconds = 0;
        }
        this.displaySeconds += 1;
      }, 1000);
    },
    pauseTimer() {
      if (this.pauseClicks !== 0) {
        this.startTimer();
        this.pauseClicks = 0;
      }
      clearInterval(this.counter);
    },
    finishTimer() {
      clearInterval(this.counter);
      this.displayHours = 0;
      this.displayMinutes = 0;
      this.displaySeconds = 0;
    },
  },
  computed: {
    currentTime() {
      return {
        hours: this.displayHours,
        minutes: this.displayMinutes,
        seconds: this.displaySeconds,
      };
    },
  },
};
</script>

<style>
a {
  cursor: pointer;
  display: block;
}

.mainTimeBox {
  padding-left: 1rem;
  padding-right: 1rem;
}

.timeBox {
  flex-basis: 100%;
  gap: 1rem;
  background-color: rgb(190, 190, 190);
  border-radius: 50px;
}

.timeBox__timeBtn,
.timeBox__profile {
  flex-basis: 100%;
  gap: 1.5rem;
}

.timeBox__timeBtn-currentTime {
  font-size: 3vh;
  text-align: center;
  flex-basis: 1;
  flex-grow: 1;
  flex-shrink: 1;
}

button {
  flex: 1 1 0;
  border: none;
}

button:nth-child(4) {
  background-color: red;
}

.timeBox__timeBtn-getIn {
  flex-basis: 1;
  flex-grow: 4;
  flex-shrink: 1;
  background-color: #5ebea3;
  color: white;
  font-size: 1.2vw;
  font-weight: 700;
}

.timeBox__profile-img {
  width: 40px;
  height: auto;
}

.timeBox__profile-name {
  flex-basis: 1;
  flex-grow: 3;
  flex-shrink: 1;
  font-size: 1.2vw;
  text-align: center;
}

img {
  width: 100%;
  height: auto;
}

nav {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

nav .menu-item {
  width: 100%;
  color: rgb(0, 0, 0);
  position: relative;
  text-align: center;
}

.menu-item a {
  padding: 10px 20px;
  display: block;
  width: 100%;
}

.menu-item a::after {
  content: "";
  display: block;
  width: 100%;
  height: 1px;
  background-color: rgb(241, 241, 241);
}

nav .menu-item.active,
nav .menu-item:hover {
  color: rgb(86, 192, 0);
  border-bottom-color: yellowgreen;
}
</style>
