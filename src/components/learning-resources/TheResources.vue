<!-- Main entry point of resources area -->

<!-- we have 2 buttons clicking on it switches b/w STORED Resources and Add REsources components-->


<template>
    <base-card>
        <base-button @click="setSelectedTab('stored-resources')" :mode="storedResButtonMode">Stored Resources</base-button>
        <base-button @click="setSelectedTab('add-resource')" :mode="addResButtonMode">Add Resource</base-button>
    </base-card>

    <!-- dynamic compo tell which component to be rendered upon clicking the above buttons -->
    <component :is="selectedTab"></component>
</template>


<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
    components : {StoredResources,
        AddResource},
    data(){
        return{
            selectedTab : 'stored-resources',
            storedResources: [
                {
                    id: 'official-guide',
                    title: 'Official Guide',
                    description: 'The official guide of VueJs',
                    link: 'https://vuejs.org',
                },
                {
                    id: 'official-guide',
                    title: 'Official Guide',
                    description: 'Google site',
                    link: 'https://google.co.in',
                },
            ],
        }
    },
    provide(){
        return {
            resources : this.storedResources
        }
    },
    computed: {
        storedResButtonMode(){
            return this.selectedTab === 'stored-resources' ? null : 'flat'
        },
        addResButtonMode(){
            return this.selectedTab === 'add-resource' ? null : 'flat'
  
        }
    },
    methods : {
        setSelectedTab(tab){
            this.selectedTab = tab;
        }
    }

}
</script>