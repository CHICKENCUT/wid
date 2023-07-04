<template>
    <div>
      <h2>Stopwatch Widget</h2>
      <p>{{ formatTime }}</p>
      <div>
        <button class="start-btn btn" @click="start" :disabled="interval">Mulai</button>
        <button class="stop-btn btn" @click="stop" :disabled="!interval">Berhenti</button>
        <button class="reset-btn btn" @click="reset">Ulangi</button>
      </div>
    </div>
  </template>
  
<style>
.stopwatch-widget {
  text-align: center;
}

h2 {
  font-size: 24px;
  margin-bottom: 10px;
  color: #333;
}

p {
  font-size: 36px;
  margin-bottom: 20px;
  color: #000000;
}

.btn {
  padding: 10px 20px;
  margin-right: 10px;
  margin-bottom: 20px;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.start-btn {
  background-color: #4caf50;
  color: #fff;
}

.stop-btn {
  background-color: #f44336;
  color: #fff;
}

.reset-btn {
  background-color: #2196f3;
  color: #fff;
}

.btn:hover {
  transform: translateY(-4px);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.btn:active {
  transform: scale(0.95);
  box-shadow: none;
}

.btn:disabled {
  background-color: #ccc;
  color: #777;
  cursor: not-allowed;
}
</style>

  <script>
  export default {
    data() {
      return {
        time: 0,
        interval: null,
      };
    },
    computed: {
      formatTime() {
        let milliseconds = this.time % 1000;
        let seconds = Math.floor((this.time / 1000) % 60);
        let minutes = Math.floor((this.time / (1000 * 60)) % 60);
        let hours = Math.floor((this.time / (1000 * 60 * 60)));
  
        return `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds
          .toString()
          .padStart(2, '0')}.${milliseconds.toString().padStart(3, '0')}`;
      },
    },
    methods: {
      start() {
        if (!this.interval) {
          this.interval = setInterval(() => {
            this.time += 10;
          }, 10);
        }
      },
      stop() {
        if (this.interval) {
          clearInterval(this.interval);
          this.interval = null;
        }
      },
      reset() {
        this.time = 0;
        clearInterval(this.interval);
        this.interval = null;
      },
    },
    beforeUnmount() {
      clearInterval(this.interval);
    },
  };
  </script>