<template>
    <v-card>
      <v-card-title>
       STUDENT INFORMATION
        <v-spacer></v-spacer>
        <v-text-field v-model="search" append-icon="mdi-magnify" label="Search" single-line hide-details></v-text-field>
      </v-card-title>
      <v-data-table :headers="headers" 
      :items="StudentData" 
      :search="search">
        <template slot="item.actions" slot-scope="{item}">
          <v-btn dark color="#43A047"><v-icon left>mdi-eye</v-icon> VIEW</v-btn>
          <v-btn dark color="#01579B"><v-icon left>mdi-pencil</v-icon> EDIT</v-btn>
          <v-btn dark color="#D32F2F"><v-icon left>mdi-trash-can</v-icon> DELETE</v-btn>
        </template>
      </v-data-table>
  
    </v-card>
  </template>
  <script>
  export default {
    name: "studentinfo",
    data() {
      return {
        search: '',
        headers: [
          {
            text: 'Student#',
            align: 'start',
            sortable: false,
            value: 'attributes.student_no',
          },
          { text: 'LastName', value: 'attributes.last_name' },
          { text: 'MiddleName', value: 'attributes.middle_name' },
          { text: 'FirtsName', value: 'attributes.first_name' },
          { text: 'Course', value: 'attributes.course' },
          { text: 'Section', value: 'attributes.section' },
          { text: 'Address', value: 'attributes.address' },
          { text: '', value: "actions" }
        ],
        StudentData: [

        ],
      }
    },

methods:{
  getStudentData() {
          this.$axios
            .get("http://localhost:1337/api/student-infos")
            .then((response) => {
              console.log(response.data.data);
              this.StudentData = response.data.data;
            })
            .catch((error) => {
              console.log(error);
            });
        },
},
mounted(){
  this.getStudentData();
},
  };
  </script>
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  <!-- <template>
      <v-container fluid>
        <v-row>
          <v-col>
            <h2>
              <v-icon>mdi-list-box</v-icon> List of Records
            </h2>
          </v-col>
    
          <v-col align="right">
            <v-btn to="/records/add" color="primary"
              ><v-icon>mdi-plus</v-icon>ADD RECORD</v-btn
            >
          </v-col>
        </v-row>
    
        <v-row>
          <v-col>
            <v-card>
              <v-card-title>
                <v-spacer></v-spacer>
                <v-spacer></v-spacer>
                <v-spacer></v-spacer>
                <v-spacer></v-spacer>
                <v-spacer></v-spacer>
                <v-spacer></v-spacer>
              </v-card-title>
              <v-data-table :headers="headers" :items="info" :search="search">
                <template slot="item.actions" slot-scope="{ item }">
                  <v-btn :to="`/records/${item.id}/view`" color="#43A047"
                    ><v-icon left>mdi-eye</v-icon>View</v-btn
                  >
                  <v-btn :to="`/records/${item.id}/edit`" dark color="#01579B"
                    ><v-icon left>mdi-pencil</v-icon>Edit</v-btn
                  >
                  <v-btn @click="showDeleteDialog(item.id)" dark color="#D32F2F"
                    ><v-icon left>mdi-trash-can</v-icon>Delete</v-btn
                  >
                </template>
              </v-data-table>
            </v-card>
          </v-col>
        </v-row>
    
        <v-dialog v-model="dialog" width="500">
          <v-sheet
            class="px-7 pt-7 pb-4 mx-auto text-center d-inline-block"
            color="blue-grey darken-3"
            dark
          >
            <div class="grey--text text--lighten-1 text-body-2 mb-4">
              Are you sure you want to delete this Information?
            </div>
    
            <v-btn  class="ma-1" color="grey" plain @click="dialog = false">
              Cancel
            </v-btn>
    
            <v-btn class="ma-1" color="error" plain @click="deleteData "
            >
              Delete
            </v-btn>
          </v-sheet>
        </v-dialog>
      </v-container>
    </template>
    
    <script>
    export default {
      layout: "default",
      name: "dashboard",
  
    
      data() {
        return {
          
          search: "",
          headers: [
            {
              text: " Student Number",
              align: "start",
              sortable: false,
              value: "attributes.id_no",
            },
            { text: "Lastname", value: "attributes.last_name" },
            { text: "Firstname", value: "attributes.first_name" },
            { text: "Middlename", value: "attributes.middle_name" },
            { text: "Section", value: "attributes.Section" },
            { text: "", value: "actions" },
          ],
          info: [],
          dialog: false,
          inmateId: null,
        };
      },
    
      methods: {
        get(dataname)() {
          this.$axios
            .get("api")
            .then((response) => {
              console.log(response.data.data);
              this.info = response.data.data;
            })
            .catch((error) => {
              console.log(error);
            });
        },
    
        showDeleteDialog(data) {
          console.log(data);
          this.dialog = true;
          this.inmateId = data;
        },
    
        deleteData() {
          this.$axios.delete(`/api/inmate-infos/${this.inmateId}`)
          .then((response)=> {
            console.log(response);
            this.dialog =false;
            this.getInmateData();
          })
          .catch((error)=>{
            console.log(error);
          });
    
        },
      },
    
      mounted() {
        this.getInmateData();
      },
    };
    </script> -->