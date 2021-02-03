<template>
	<div>
		<Hero />
	</div>
</template>

<script>
import Hero from '@/components/Hero'
import axios from 'axios'

export default {
	name: 'Home',
	components: {
		Hero
	},
	data() {
		return {
			stats: []
		}
	},
	methods: {
		async fetchWeightStats() {
			try {
				const statsData = await axios.get('http://localhost:5000/api/v1/stats')
				this.stats = statsData.data
			} catch (error) {
				console.log(error)
			}
		}
	},
	created() {
		this.fetchWeightStats()
	}
}
</script>

<style></style>
