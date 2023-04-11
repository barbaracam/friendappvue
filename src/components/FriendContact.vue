<template>
    <li>
        <h2>{{fullName}}</h2>
        <button @click="toggleDetails">Show Details</button>
        <ul v-if="detailsAreVisible">
            <li><strong>Phone: </strong>{{ phoneNumber}}</li>
            <li><strong>Email: </strong>{{ emailAddress}}</li>
        </ul>
    </li>


    
</template>

<script>
export default {
  // props should have same name as data props
  props:[
    'fullName',
    'phoneNumber',
    'emailAddress'    
    ],
    data() {
      return {
        detailsAreVisible:false,
        friend: {
          id: "Gordis",
          name: "Sam",
          lastname: "Biden",
          phone:"281 289 5565",
          email: "sam@hotmail.com",
        },        
      };
    },
    methods:{
        toggleDetails(){
          this.detailsAreVisible = !this.detailsAreVisible;  
        }
    }
  };
  </script>