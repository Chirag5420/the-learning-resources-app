<template>
    <base-card>
        <base-button @click="setSelectedTab('stored-resources')" :mode="storedResButtonMode">Stored Resources</base-button>
        <base-button @click="setSelectedTab('add-resource')" :mode="addResButtonMode">Add Resources</base-button>
    </base-card>
    
    <keep-alive>
        <component :is="selectedTab" 
        @delete="deleteResource"></component>
    </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
    components: {
        'stored-resources': StoredResources,
        'add-resource': AddResource
    },
    data() {
        return {
            selectedTab: 'stored-resources',
            storedResources: [
                {
                    id: 'official-guide', 
                    title: 'Official Guide', 
                    description: 'The official Vue.js documentation',
                    link: 'https://vuejs.org'
                }, 
                {
                    id: 'google', 
                    title: 'Google', 
                    description: 'Learn to Google...',
                    link: 'https://google.com'
                }
            ],
        }
    },
    methods: {
        setSelectedTab(tab) {
            this.selectedTab = tab
        },
        addResource(newResource) {
            this.storedResources.unshift(newResource)
            this.selectedTab = 'stored-resources'
        },
        removeResource(resId) {
            const resIndex = this.storedResources.findIndex(res => res.id === resId);
            this.storedResources.splice(resIndex, 1);
        }
    },
    provide() {
        return {
            storedResources: this.storedResources,
            addResource: this.addResource,
            deleteResource: this.removeResource
        }
    },
    computed: {
        storedResButtonMode() {
            return this.selectedTab === 'stored-resources' ? null : 'flat';
        },
        addResButtonMode() {
            return this.selectedTab === 'add-resource' ? null : 'flat';
        }
    }
}
</script>