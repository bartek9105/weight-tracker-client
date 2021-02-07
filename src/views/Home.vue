<template>
	<div>
		<Hero />
		<Chart v-if="!isLoading" :chart-stats="chartdata" />
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
			chartdata: {
				labels: [],
				datasets: [
					{
						label: 'Weight',
						backgroundColor: '#f87979',
						data: []
					}
				]
			}
		}
	},
	methods: {
		async fetchWeightStats() {
			try {
				const statsData = await axios.get('http://localhost:5000/api/v1/stats')
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
			})
		}
	},
	mounted() {
		this.fetchWeightStats()
	}
}
</script>

<style></style>
