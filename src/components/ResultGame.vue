<template>
		<p>Result is {{score}}ms</p>
		<div v-if="score <= 200">
			<h3>OMG! Amazing speed...</h3>
		</div>
		<div v-else-if="score > 200 && score < 600">
			<h3>Grade...Every can do it. You are normal</h3>
		</div>
		<div v-else>
			<h3>Oop! Too slow...Try again</h3>
		</div>
</template>
	
<script>
export default{
	props: [
		"score"
	]
}	
</script>
	
<style>
	
</style>