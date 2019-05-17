<template>
    <div class="component">
        
        <h1>Componente de usuario (padre)</h1>
        <p>Hola!</p>
        <button @click="changeName">Cambiar nombre</button>
        <p>Mi nombre es {{ name }}</p>
        <p>Mi edad es {{ age }}</p>
        <hr>


        <div class="row">
            <div class="col-xs-12 col-sm-6">
                <app-user-detail
                        :myName="name"
                        @nameWasReset="name = $event"
                        :resetFn="resetName"
                        :userAge="age"
                        
                    ></app-user-detail>
            </div>


            <div class="col-xs-12 col-sm-6">
                <app-user-edit
                        :userAge="age"
                        @ageWasEdited="age = $event"
                ></app-user-edit>
            </div>

        </div>

        
    </div>
</template>

<script>
    import UserDetail from './UserDetail.vue';
    import UserEdit from './UserEdit.vue';

    export default {
        data: function () {
            return {
                name: 'Leslie',
                age: 19 //by default
            };
        },
        methods: {
            changeName() {
                this.name = 'Marie';
            },
            resetName() {
                this.name = 'Leslie';
            }
        },
        components: {
            appUserDetail: UserDetail,
            appUserEdit: UserEdit
        }
    }
</script>

<style scoped>
    div {
        background-color: lightblue;
    }
</style>
