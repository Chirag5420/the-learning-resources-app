<template>
    <ul>
        <learning-resource
            v-for="resource in storedResources" 
            :key="resource.id"
            :resource-id="resource.id"
            :resource-title="resource.title"
            :resource-description="resource.description"
            :resource-link="resource.link"
        ></learning-resource>
    </ul>
</template>

<script>
import LearningResource from './LearningResource.vue'

export default {
    inject: ['storedResources'],
    components: {
        'learning-resource': LearningResource
    }
}
</script>

<style scoped>
ul {
    list-style: none;
    margin: 0;
    padding: 0;
    margin: auto;
    max-width: 40rem;
}
</style>