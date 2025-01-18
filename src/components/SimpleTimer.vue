<template>
	<div class="flex flex-col justify-content content-center text-center">
		<p class="text-3xl">{{ hoursAsString }}:{{ minutesAsString }}:{{ secondsAsString }}</p>
		<div class="space-x-2">
			<button class="h-8 w-16 border-2 border-transparent rounded bg-green-600 hover:bg-green-800 text-white" @click="start">Start</button>
			<button v-if="!isPaused" class="h-8 w-16 border-2 border-transparent rounded bg-blue-600 hover:bg-blue-800 text-white" @click="pause">Pause</button>
			<button v-else class="h-8 w-16 border-2 border-transparent rounded bg-blue-600 hover:bg-blue-800 text-white" @click="resume">Resume</button>
			<button class="h-8 w-16 border-2 border-transparent rounded bg-red-600 hover:bg-red-800 text-white" @click="stop">Stop</button>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			seconds: 0,
			minutes: 0,
			hours: 0,
			secondsAsString: '00',
			minutesAsString: '00',
			hoursAsString: '00',
			isPaused: false,
			timer: null,
		};
	},
	methods: {
		start() {
			this.isPaused = false;
			this.timer = setInterval(() => {
				this.seconds++;
				if (this.seconds > 59) {
					this.seconds = 0;
					this.minutes++;
				}
				if (this.minutes > 59) {
					this.minutes = 0;
					this.hours++;
				}
				if (this.seconds < 10) {
					this.secondsAsString = '0' + this.seconds;
				} else {
					this.secondsAsString = this.seconds;
				}
				if (this.minutes < 10) {
					this.minutesAsString = '0' + this.minutes;
				} else {
					this.minutesAsString = this.minutes;
				}
				if (this.hours < 10) {
					this.hoursAsString = '0' + this.hours;
				} else {
					this.hoursAsString = this.hours;
				}
			}, 1000);
		},
		stop() {
			this.seconds = 0;
			this.minutes = 0;
			this.hours = 0;
			this.secondsAsString = '00';
			this.minutesAsString = '00';
			this.hoursAsString = '00';
			this.isPaused = false;
			clearInterval(this.timer);
			this.timer = null;
		},
		pause() {
			this.isPaused = true;
			clearInterval(this.timer);
			this.timer = null;
		},
		resume() {
			this.isPaused = false;
			this.timer = this.start();
		}
	},
};
</script>

<style>
</style>
