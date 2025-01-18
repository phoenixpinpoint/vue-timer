<template>
	<div class="flex flex-col flex-wrap w-screen h-screen justify-center content-center">
		<img alt="Vue logo" src="./assets/logo.png">
		<SimpleTimer />
	</div>
</template>

<script>
import SimpleTimer from './components/SimpleTimer.vue'

export default {
  name: 'App',
  components: {
	SimpleTimer
  }
}
</script>

<style>

</style>
