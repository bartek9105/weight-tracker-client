<script>
import { Line } from 'vue-chartjs'

export default {
	name: 'Chart',
	extends: Line,
	props: {
		chartStats: {
			type: Object,
			default: () => {}
		}
	},
	data() {
		return {
			options: {
				responsive: true,
				maintainAspectRatio: false
			}
		}
	},
	mounted() {
		this.renderChart(this.chartStats, this.options)
	}
}
</script>

<style></style>
