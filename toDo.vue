<template>
<v-app style='margin:30px'>
    <v-card>
        <!--panel header-->
        <v-card-title
            class='headline primary'
            primary-title style='color: white;'>
           <v-icon color='white'>mdi-menu</v-icon>
                To Do
                <!--Adding dialog box-->
                <v-dialog
                    v-model="dialog"
                    width="40%"
                >
                <template v-slot:activator="{on}">
                    <v-row justify="end">
                        <v-btn
                            justify="right"
                            color="info"
                            v-on="on"
                        >
                        <v-icon>mdi-plus-circle</v-icon>
                            Add
                        </v-btn>
                    </v-row> 
                </template>
                <v-card>
                <!--dialog box appears-->
                <!--dialog header-->
                <v-card-title
                    class="headline info"
                    primary-title style='color: white;'
                >
                <v-icon color='white'>mdi-plus-circle</v-icon>
                        Add Task
                
                </v-card-title>
                <br>
                <!--dialog content-->
                <v-card-text>
                    <!--title-->
                    <v-text-field
                        v-model="title"
                        id="title"
                        filled
                        outlined
                        background-color="#FFF9C4"
                        label="Type title..."
                        :rules="[()=> !!title || 'The title is empty!']"
                    >
                    </v-text-field>
                    <!--description-->
                    <v-text-field
                        v-model="description"
                        id="description"
                        filled
                        outlined
                        background-color="#FFF9C4"
                        label="Type description..."
                        :rules="[()=> !!description || 'This description is empty!']"
                        >
                    </v-text-field>
                    <!--calendar-->
                    <v-menu
                        v-model="menu"
                        :close-on-content-click="false"
                        :nudge-right="40"
                        transition="scale-transition"
                        offset-y
                        min-width="auto"
                    >
                    <template v-slot:activator="{on,attrs}">
                        <v-text-field
                            v-model="date"
                            id="date"
                            label="Deadline"
                            filled
                            hint="MM/DD/YYYY"
                            outlined
                            background-color="#FFF9C4"
                            append-icon="mdi-calendar"
                            readonly
                            v-bind="attrs"
                            v-on="on"
                        ></v-text-field>
                    </template>
                        <v-date-picker
                        id="Deadline"
                        v-model="date"
                        @change="menu = false"
                        ></v-date-picker>
                    </v-menu>
                    <!--radio-->
                    <v-radio-group
                    v-model="row"
                    row
                    >
                    <p class="font-weight-bold">
                        Priority:
                    </p>
                    <v-radio
                        label="Low"
                        value="radio-01"
                    ></v-radio>
                    <v-radio
                        label="Medium"
                        value="radio-02"
                    ></v-radio>
                    <v-radio
                        label="High"
                        value="radio-03"
                    ></v-radio>
                    </v-radio-group>
                    
                </v-card-text>
                    <!--add button-->
                    <v-row justify="center">
                    <v-btn
                        color="info"
                        width="45%"
                        @click="dialog = false"
                    >
                    <v-icon>mdi-plus-circle</v-icon>
                        Add 
                    </v-btn>
                    <!--cancel button-->
                    <v-btn
                        color="error"
                        width="45%"
                        @click="dialog = false"
                    >
                    <v-icon>mdi-close-circle</v-icon>
                        Cancel
                    </v-btn>
                    </v-row>
                </v-card>
                </v-dialog>
        </v-card-title>
        <!--panel body-->
        <v-simple-table style='margin: 20px;'>
            <template v-slot:default>

            <!--table header-->
                <thead>
                <tr>
                    <th class="text-auto">
                        Task
                    </th>
                    <th class="text-auto">
                        Description
                    </th>
                    <th class="text-auto">
                        Deadline
                    </th>
                    <th class="text-auto">
                        Priority
                    </th>
                    <th class="text-auto">
                        Is Complete?
                    </th>
                    <th class="text-auto">
                        Action
                    </th>
                </tr>
                </thead>
            <!--table body-->
                <tbody>
                    <tr>
                        <td>{{body}}</td>
                    </tr>
                </tbody>
            </template>
        </v-simple-table>
    </v-card>
</v-app>
</template>
<script>
//master
    export default {
    //life cycles
        created(){},
    //methods
        methods: {}, 
    //watchers
        watch: {},
    //computed
        computed: {},
    //global vars
          data: global => ({
            date: '',
            header: '',
            body: '',
            dialog: false,
            errors: [],
            title: null,
            description: null,
            menu:false,
            modal: false,
            row: null,
        }),
    }
</script>