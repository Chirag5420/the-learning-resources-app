<template>
    <li>
        <base-card>
            <div>
                <header>
                    <h3>{{ resourceTitle }}</h3>
                    <base-button mode="flat" @click="deleteResource(resourceId)">Delete</base-button>
                </header>
            </div>
            <p>{{ resourceDescription }}</p>
            <nav>
                <a :href="resourceLink">View Resource</a>
            </nav>
        </base-card>
    </li>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue'
export default {
  components: { BaseButton },
  props: ['resourceId', 'resourceTitle', 'resourceDescription', 'resourceLink'], 
  inject: ['deleteResource']
}
</script>

<style scoped>
li {
    margin: auto;
    max-width: 40rem;
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

h3 {
    font-size: 1.25rem;
    margin: 0.5rem 0;
}

p {
    margin: 0.5rem 0;
}

a {
    text-decoration: none;
    color: #ce5c00;
}

a:hover,
a:active {
    color: #c89300;
}
</style>