<template>
    <div class="component">
        <h3>Editar usuario aqui (hijo)</h3>
        <p>Editame!</p>
        <p>Edad del usuario: {{ userAge }}</p>
        <button @click="editAge">Editar edad</button>
    </div>
</template>

<script>
    import {eventBus} from '../main';

    export default {
        props: ['userAge'],
        methods: {
            editAge() {
                this.userAge = 20;
//                this.$emit('ageWasEdited', this.userAge);
//                eventBus.$emit('ageWasEdited', this.userAge);
                eventBus.changeAge(this.userAge);
            }
        }
    }
</script>

<style scoped>
    div {
        background-color: lightgreen;
    }
</style>