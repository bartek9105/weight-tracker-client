<template>
	<header class="header">
		<form class="header__weight-stats-form">
			<div class="input-container">
				<label for="weight" class="header__weight-stats-form__label"
					>Weight</label
				>
				<input
					type="number"
					name="weight"
					class="header__weight-stats-form__input"
					v-model="stats.weight"
				/>
			</div>
			<div class="input-container">
				<label for="bmi" class="header__weight-stats-form__label">BMI</label>
				<input
					type="number"
					name="bmi"
					class="header__weight-stats-form__input"
					v-model="stats.bmi"
				/>
			</div>
			<div class="input-container">
				<label for="fat" class="header__weight-stats-form__label">Fat</label>
				<input
					type="number"
					name="fat"
					class="header__weight-stats-form__input"
					v-model="stats.fat"
				/>
			</div>
			<div class="input-container">
				<label for="muscleMass" class="header__weight-stats-form__label"
					>Muscle Mass</label
				>
				<input
					type="number"
					name="muscleMass"
					class="header__weight-stats-form__input"
					v-model="stats.muscleMass"
				/>
			</div>
			<div class="input-container">
				<label for="water" class="header__weight-stats-form__label"
					>Water</label
				>
				<input
					type="number"
					name="water"
					class="header__weight-stats-form__input"
					v-model="stats.water"
				/>
			</div>
		</form>
		<p v-if="error" class="header__error">{{ error }}</p>
		<Button @click.native="addStats">Add</Button>
	</header>
</template>

<script>
import Button from '@/components/Button'
import axios from 'axios'

export default {
	name: 'Hero',
	components: {
		Button
	},
	data() {
		return {
			stats: {
				weight: null,
				bmi: null,
				fat: null,
				muscleMass: null,
				water: null
			},
			error: null
		}
	},
	methods: {
		async addStats() {
			try {
				await axios.post(`${process.env.VUE_APP_API_URL}/stats`, this.stats)
				this.error = null
			} catch (error) {
				this.error = error.response.data.error
			}
		}
	}
}
</script>

<style lang="scss" scoped>
.header {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	width: 100%;
	background-color: #fbab7e;
	background-image: linear-gradient(62deg, #fbab7e 0%, #f7ce68 100%);
	padding: 3rem 1rem;
	&__weight-stats-form {
		display: flex;
		justify-content: center;
		flex-wrap: wrap;
		margin-bottom: 3rem;
		.input-container {
			display: flex;
			flex-direction: column;
			margin-right: 1rem;
			margin-bottom: 1rem;
		}
		&__label {
			color: #fff;
			margin-bottom: 1rem;
			font-weight: 500;
		}
		&__input {
			border: 0;
			border-radius: 5px;
			padding: 0 0.5rem;
			height: 35px;
		}
	}
	&__error {
		color: #fff;
		margin-bottom: 1rem;
	}
}
</style>
