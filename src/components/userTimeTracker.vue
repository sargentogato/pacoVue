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
      <svg id="chart" width="3" height="40">
        <line x1="20" y1="20" x2="20" y2="130"></line>
      </svg>
      <div class="timeBox__profile flex justify-between items-center p-4">
        <div class="timeBox__profile-img">
          <img src="../assets/profile.png" alt="" />
        </div>
        <h2 class="timeBox__profile-name">Marlon Velásquez</h2>
        <drop-down :itemsMenu="services" :time="currentTime" :users="workers" />
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
      workers: ["Marlon Velásquez"],
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
  background-color: hsl(0, 0%, 85%);
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

svg#chart {
  background: rgb(165, 165, 165);
}

#chart line {
  stroke-width: 1;
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
</style>
