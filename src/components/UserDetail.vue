<template>

    <div class="component">

        <h3>Ver los detalles aqui (hijo)</h3>
        <p>Detalles</p>
        <p>Nombre de usuario revertido: {{ switchName() }}</p>
        <p>Edad del usuario: {{ userAge }}</p>

        <button @click="resetName">Reiniciar nombre (event)</button>
        <button @click="resetFn()">Reiniciar nombre (callback)</button>
    </div>

</template>


<script>
    import { eventBus } from '../main';

    export default {
        props: {
            myName: {
                type: String
            },
            resetFn: Function,
            userAge: Number
        },
        methods: {
            switchName() {
                return this.myName.split("").reverse().join("");
            },
            resetName() {
                this.myName = 'Leslie';
                this.$emit('nameWasReset', this.myName);
            }
        },
        created() {
            eventBus.$on('ageWasEdited', (age) => {
                this.userAge = age;
            });
        }
    }
</script>


<style scoped>
    div {
        background-color: lightcoral;
    }
</style>
