<template>
	<div class="accordion" id="accordionExample">
		<div class="accordion-item" v-for="(item, index) of data" :key="index">
			<h2 class="accordion-header" id="headingOne">
				<button class="accordion-button collapsed" type="button" data-bs-toggle="collapse"
					:data-bs-target="'#collapse' + index" aria-expanded="true" :aria-controls="'collapse' + index">
					{{ item.title }}
				</button>
			</h2>
			<div :id="'collapse' + index" class="accordion-collapse collapse" data-bs-parent="#accordionExample">
				<span class="accordion-label">
					{{ item.label }}
				</span>
				<ul class="questions-list">
					<li class="questions-list__item" v-for="(question, idx) of item.question" :key="idx">
						{{ question.label }}
					</li>
				</ul>
			</div>
		</div>
</div>
</template>

<script setup>
import data from './mockedData/questionsData.json'
</script>


<style lang="scss" scoped>
.accordion {
	width: 600px;
	box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.02), 0px 4px 17px rgba(0, 0, 0, 0.14), 0px 4px 22px rgba(0, 0, 0, 0.12);
	border-radius: 8px;
	margin: 0 auto;
}

.accordion-label {
	font-weight: 800;
	font-size: 16px;
	line-height: 24px;
	padding-left: 24px;
	margin-bottom: 8px;

	color: #2B41B7;
}

.accordion-button {
	color: #0D2A54;
	background: #FAF8F6;
	font-style: normal;
	font-weight: 800;
	font-size: 16px;
	line-height: 24px;
	box-shadow: 0 0 0 0 rgba(0, 0, 0, 0) !important;
	padding: 24px 31px 0 24px;
}

.accordion-button.collapsed {
	background: white;
	color: #0D2A54;
	padding: 24px 31px 24px 24px;
}

.collapse,
.collapsing {
	background: #FAF8F6;
	padding: 8px 24px 24px 12px;
}

.questions-list {
	list-style-image: url('../assets/bullet.svg');
	margin-bottom: 0;
}

.questions-list__item {
	font-style: normal;
	font-weight: 600;
	font-size: 14px;
	line-height: 24px;
	color: #0D2A54
}

.questions-list__item:not(:last-child) {
	margin-bottom: 8px;
}

@media screen and (max-width: 600px) {
	.accordion {
		width: 500px;
	}
}

@media screen and (max-width: 500px) {
	.accordion {
		width: 400px;
	}

	.accordion-label {
		font-size: 13px;
	}
}

@media screen and (max-width: 400px) {
	.accordion {
		width: 300px;
	}

	.collapse,
	.collapsing {
		padding: 8px 24px 24px 0;
	}

	.accordion-button {
		padding: 16px 23px 0 16px;
	}

	.accordion-button.collapsed {
		padding: 16px 23px 16px 16px;
	}

	.questions-list {
		padding-right: 16px;
	}
}
</style>
