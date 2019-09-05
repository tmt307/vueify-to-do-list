<template>
    <v-row>
        <v-col cols="12" sm="6" offset-sm="3">
            <v-card>
                <v-toolbar color="blue darken-4">
                    <v-toolbar-title class="white--text">To Do List</v-toolbar-title>
                    <div class="flex-grow-1"></div>



                    <v-btn icon>
                        <v-icon>mdi-view-module</v-icon>
                    </v-btn>
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

                <v-list>
                    <v-list-item v-for="item in todolist" :key="item.title" @click="">

                        <v-list-item-content>
                            <v-list-item-title>{{ item.title }}</v-list-item-title>
                        </v-list-item-content>

                        <v-list-item-action>
                            <v-btn color="gray accent-4" dark>
                                <v-icon dark>mdi-pencil </v-icon> <span class="m-2">Edit</span>

                            </v-btn>
                        </v-list-item-action>

                        <v-list-item-action>
                            <v-btn  color="red accent-4" dark>
                                <v-icon dark>mdi-delete-circle </v-icon> <span class="m-2">Delete</span>

                            </v-btn>
                        </v-list-item-action>
                    </v-list-item>
                </v-list>

                    <v-dialog v-model="dialog" max-width="500px">
                        <v-card>
                            <v-card-text>
                                <v-text-field label="Task Name"></v-text-field>
                            </v-card-text>
                            <v-card-actions>
                                <div class="flex-grow-1"></div>
                                <form @submit.prevent="addtodo">
                                    <v-input v-model="todo"type="text" name="newtodo" value="" id="newtodo" />


                                    <v-btn text color="primary" @click="dialog = false" name="button" type="submit">add</v-btn>
                                </form>
                            </v-card-actions>
                        </v-card>
                    </v-dialog>
            </v-card>
        </v-col>
    </v-row>
</template>

<script>
    export default {
        data() {
            return {
                dialog: false,
                                todolist: [
                    { iconClass: 'blue white--text', title: 'Vacation itinerary' },
                ],
            }

        },
      methods: {
        addtodo() {
            console.log('form sub');t
        }
    }
    }

</script>