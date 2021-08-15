<template>
	<base-card>
		<base-button @click="setSelectedTab('stored-resources')">Stored Resource</base-button>
		<base-button @click="setSelectedTab('add-resources')">Add Resource</base-button>
		<component :is="selectedTab"></component>
	</base-card>
</template>

<script>
	import StoredResources from "./StoredResources.vue";
	import AddResources from "./AddResources.vue";
	export default {
		components: {
			StoredResources,
			AddResources
		},
		data() {
			return {
				selectedTab: "stored-resources",
				storedResources: [
					{
						id: "official guide",
						title: "official guide",
						description: "official guide",
						link: "https://www.google.com/"
					},
					{
						id: "Home guide",
						title: "official guide",
						description: "official guide",
						link: "https://www.google.com/"
					}
				]
			};
		},
		methods: {
			setSelectedTab(tab) {
				this.selectedTab = tab;
			}
		},
		provide(){
			return{
				resources:this.storedResources
			}
		}
	};
</script>
<style scoped>
</style>