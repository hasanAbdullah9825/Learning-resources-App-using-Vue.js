<template>
	<base-card>
		<base-button @click="setSelectedTab('stored-resources')"
			>Stored Resource</base-button
		>
		<base-button @click="setSelectedTab('add-resources')"
			>Add Resource</base-button
		>
		<keep-alive>
			<component :is="selectedTab"></component>
		</keep-alive>
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
			},
			addResource(enteredTitle, enteredDescription, enteredLink) {
				const newResource = {
					id: new Date().toISOString,
					title: enteredTitle,
					description: enteredDescription,
					link: "https://"+enteredLink
				};
				this.storedResources.unshift(newResource);
				this.selectedTab="stored-resources";
			},
			removeResource(removeId){
				const index= this.storedResources.findIndex(res=>removeId===res.id);
				this.storedResources.splice(index,1);
			}
		},
		provide() {
			return {
				resources: this.storedResources,
				addResource:this.addResource,
				removeResource:this.removeResource
			};
		}
	};
</script>
<style scoped>
</style>