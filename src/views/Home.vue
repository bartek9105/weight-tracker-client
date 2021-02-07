<template>
	<div>
		<Hero class="hero" />
		<Chart v-if="!isLoading" :chart-stats="chartdata" class="chart" />
	</div>
</template>

<script>
import Hero from '@/components/Hero'
import Chart from '@/components/Chart'
import axios from 'axios'

export default {
	name: 'Home',
	components: {
		Hero,
		Chart
	},
	data() {
		return {
			isLoading: true,
			stats: [],
			addedStats: {},
			chartdata: {
				labels: [],
				datasets: [
					{
						label: 'Weight',
						backgroundColor: '#f87979',
						data: []
					},
					{
						label: 'Fat',
						backgroundColor: '#fbab7e',
						data: []
					},
					{
						label: 'Muscles',
						backgroundColor: '#f345f1',
						data: []
					}
				]
			}
		}
	},
	methods: {
		async fetchWeightStats() {
			try {
				const statsData = await axios.get(
					`${process.env.VUE_APP_API_URL}/stats`
				)
				this.stats = statsData.data.stats
				this.setChartData()
				this.isLoading = false
			} catch (error) {
				console.log(error)
			}
		},
		setChartData() {
			this.stats.map((statsEl) => {
				this.chartdata.labels.push(new Date(statsEl.createdAt).toDateString())
				this.chartdata.datasets[0].data.push(statsEl.weight)
				this.chartdata.datasets[1].data.push(statsEl.fat)
				this.chartdata.datasets[2].data.push(statsEl.muscleMass)
			})
		},
		emitedStats(stats) {
			this.addedStats = stats
		}
	},
	mounted() {
		this.fetchWeightStats()
	}
}
</script>

<style>
.hero {
	margin-bottom: 5rem;
}
</style>
