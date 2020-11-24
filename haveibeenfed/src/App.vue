<template>
  <div>
    <h1>Freya {{ status }} been fed</h1>
    <h2>Last feeding was: {{ lastFeed }}</h2>
    <h2>
      Feeding Alerts
      <label class="switch">
        <input type="checkbox" v-model="feedingAlerts" />
        <span class="slider round"></span>
      </label>
    </h2>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function () {
    return {
      status: "has not",
      feedingAlerts: false,
      lastFeed: new Date().toDateString(),
    };
  },
  created: function () {
    this.status = "has";
    this.lastFeed = new Date().toDateString();
    this.feedingAlerts = false;
  },
  watch: {
    feedingAlerts: function (newValue) {
      console.log("feeding alerts", newValue);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: #2196f3;
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196f3;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
</style>
