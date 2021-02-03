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
				/>
			</div>
			<div class="input-container">
				<label for="bmi" class="header__weight-stats-form__label">BMI</label>
				<input
					type="number"
					name="bmi"
					class="header__weight-stats-form__input"
				/>
			</div>
			<div class="input-container">
				<label for="fat" class="header__weight-stats-form__label">Fat</label>
				<input
					type="number"
					name="fat"
					class="header__weight-stats-form__input"
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
				/>
			</div>
		</form>
		<Button>Add</Button>
	</header>
</template>

<script>
import Button from '@/components/Button'

export default {
	name: 'Hero',
	components: {
		Button
	}
}
</script>

<style lang="scss" scoped>
.header {
	width: 100%;
	height: 300px;
	display: flex;
	justify-content: center;
	align-items: center;
	background-color: #fbab7e;
	background-image: linear-gradient(62deg, #fbab7e 0%, #f7ce68 100%);
	&__weight-stats-form {
		display: flex;
		justify-content: space-between;
		flex-wrap: wrap;
		padding: 0 1rem;
		.input-container {
			display: flex;
			flex-direction: column;
			margin-right: 1rem;
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
}
</style>
