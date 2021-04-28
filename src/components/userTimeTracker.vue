<template>
  <div class="mainTimeBox flex justify-center mt-8 w-4/5 pt-4 pb-8">
    <div class="timeBox flex justify-between items-center pax-4">
      <div class="timeBox__timeBtn flex justify-between items-center p-4">
        <div class="timeBox__timeBtn-currentTime">10:25:04</div>
        <button class="timeBox__timeBtn-getIn">Entrar</button>
      </div>

      <div class="timeBox__profile flex justify-between items-center p-4">
        <div class="timeBox__profile-img">
          <img src="../assets/profile.png" alt="" />
        </div>
        <ul class="timeBox__profile-nav">
          Marlon Velasquez
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "userTimeTracker",
};
</script>

<style>
.timeBox {
  flex-basis: 100%;
  gap: 1rem;
}

.timeBox__timeBtn,
.timeBox__profile {
  flex-basis: 50%;
  /* display: flex; */
  /* justify-content: space-between; */
  /* align-items: center; */
  /* padding: 1rem; */
  gap: 1.5rem;
  border: 1px solid black;
}

.timeBox__timeBtn-currentTime {
  flex-basis: 1;
  flex-grow: 1;
  flex-shrink: 1;
}

.timeBox__timeBtn-getIn {
  flex-basis: 1;
  flex-grow: 4;
  flex-shrink: 1;
  padding: 0.5rem;
  border-radius: 25px;
}

.timeBox__profile-img {
  width: 40px;
  height: auto;
}

.timeBox__profile-nav {
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
