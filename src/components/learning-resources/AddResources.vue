<template>
	<teleport to="body">
		<base-dialog
			v-if="inputIsInvalid"
			title="Something error"
			@close="confirmError"
		>
			<template #default>
				<p>At least one input missing</p>
			</template>

			<template #actions>
				<base-button @click="confirmError">Ok</base-button>
			</template>
		</base-dialog>
			</teleport>
		<base-card>
			<form @submit.prevent="submitData()">
				<div class="form-group">
					<label for="title">Title</label>
					<input type="text" id="title" name="title" ref="titleInput" />
				</div>

				<div class="form-group">
					<label for="description">Description</label>
					<input
						type="text"
						id="description"
						name="description"
						ref="descriptionInput"
					/>
				</div>

				<div class="form-group">
					<label for="link">Link</label>
					<input type="" id="link" name="link" ref="linkInput" />
				</div>

				<div>
					<base-button type="submit">
						Add Resource
					</base-button>
				</div>
			</form>
		</base-card>
	
</template>


<script>
	import BaseCard from "../UI/BaseCard.vue";
	export default {
		components: {
			BaseCard
		},
		data() {
			return {
				inputIsInvalid: false
			};
		},
		methods: {
			submitData() {
				const enteredTitle = this.$refs.titleInput.value;
				const enteredDescription = this.$refs.descriptionInput.value;
				const enteredLink = this.$refs.linkInput.value;

				if (
					enteredTitle.trim() == "" ||
					enteredDescription.trim() == "" ||
					enteredLink == ""
				) {
					this.inputIsInvalid = true;
					return;
				}
				this.addResource(enteredTitle, enteredDescription, enteredLink);
			},
			confirmError() {
				this.inputIsInvalid = false;
			}
		},
		inject: ["addResource"]
	};
</script>

<style scoped>
	label {
		font-weight: bold;
		display: block;
		margin-bottom: 0.5rem;
	}

	input,
	textarea {
		display: block;
		width: 100%;
		font: inherit;
		padding: 0.15rem;
		border: 1px solid #ccc;
	}

	input:focus,
	textarea:focus {
		outline: none;
		border-color: #3a0061;
		background-color: #f7ebff;
	}

	.form-control {
		margin: 1rem 0;
	}
</style>