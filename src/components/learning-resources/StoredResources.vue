<template>
<ul>
<learning-resources v-for="res in resources" :key="res.id" 
:title="res.title"
:description="res.description" 
:link="res.link">

</learning-resources>
</ul>
</template>

<script>
import LearningResources from "./LearningResources.vue"
export default {
    components:{
   LearningResources
    },
    props:['resources']
}
</script>