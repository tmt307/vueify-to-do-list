<template>
    <v-row>
        <v-col cols="12" sm="6" offset-sm="3">
            <v-card>
                <v-toolbar color="blue darken-4">
                    <v-toolbar-title class="white--text">  {{title}}</v-toolbar-title>
                    <div class="flex-grow-1"></div>

                    <template v-slot:extension>
                        <v-btn fab
                               color="blue darken-1"
                               bottom
                               left
                               absolute
                               @click="dialog = !dialog">
                            <v-icon>mdi-plus</v-icon>
                        </v-btn>
                    </template>
                </v-toolbar>

                <v-col cols="12" >
                    <v-list>
                        <v-alert v-model="alertadd" color="green" dismissible>
                            The task has been added successfully
                        </v-alert>

                        <v-alert v-model="alertdelete" color="red" dismissible>
                            The task has been deleted successfully
                        </v-alert>

                        <v-list-item v-for="todo in todolist">

                            <v-list-item-content>
                                <v-list-item-title :class="{ done: todo.done}"> {{todo.title}} </v-list-item-title>
                            </v-list-item-content>

                            <v-list-item-action>
                                <v-btn class=" mr-4" color=" green accent-4" dark>
                                    <v-checkbox class="mr-2" type="checkbox" v-model="todo.done"></v-checkbox>
                                    Completed
                                </v-btn>
                            </v-list-item-action>

                            <v-list-item-action>
                                <v-btn @click="dialog2 = !dialog" color="blue" dark>
                                    <v-icon>mdi-pencil </v-icon> <span class="m-2">Edit</span>
                                </v-btn>
                            </v-list-item-action>

                            <v-list-item-action @click="deletetodo(todo)" >
                                <v-btn  @click="alertdelete = true" color="red accent-4" dark>
                                    <v-icon dark>mdi-delete-circle </v-icon> <span class="m-2">Delete</span>
                                </v-btn>
                            </v-list-item-action>
                        </v-list-item>

                    </v-list>
                </v-col>

                <v-dialog v-model="dialog" max-width="500px">
                    <v-card>
                        <v-card-actions>
                            <div class="flex-grow-1">
                                <form @submit.prevent="todoformaddmethod">
                                    <v-text-field required v-model="newtodo" type="text" name="newtodo" value="2" id="newtodo" label="Task Name"></v-text-field>
                                    <v-btn color="primary" name="button" type="submit" @click="alertadd = true">add</v-btn>
                                    <v-btn color="red" @click="dialog = false">  Close</v-btn>
                                </form>
                            </div>
                        </v-card-actions>
                    </v-card>
                </v-dialog>

                <v-dialog v-model="dialog2" max-width="500px">
                    <v-card>
                        <v-card-actions>
                            <div class="flex-grow-1">
                                <form @submit.prevent="todoformaddmethod">

                                    <v-text-field required v-model="model" type="text" name="newtodo" value="test" ></v-text-field>

                                    <v-btn color="green" name="button" type="submit">Edit</v-btn>

                                    <v-btn color="red" @click="dialog = false">  Close</v-btn>
                                </form>
                            </div>
                        </v-card-actions>
                    </v-card>
                </v-dialog>
            </v-card>
        </v-col>
    </v-row>
</template>

<style>

 .done {
        text-decoration: line-through
    }

</style>

<script>


    export default {

        data() {
            return {
                model: "{{todo.title}}",
                dialog: false,
                dialog2: false,
                alertadd: false,
                alertdelete: false,
                title: 'To do list',
                newtodo: '',
                todolist: []

            }
        },
        methods: {
            todoformaddmethod() {
                this.todolist.push({
                    title: this.newtodo,
                    done: false,
                });
                this.newtodo = '';
            },
            deletetodo(todo) {
                const todoIndex = this.todolist.indexOf(todo);
                this.todolist.splice(todoIndex, 1);

            }
        }
    }

</script>