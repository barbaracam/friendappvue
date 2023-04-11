<template>
    <li>
        <h2>{{fullName}} {{isFavorite ? '(Favorite)' : ''}}</h2>
        <button @click="toggleDetails">{{detailsAreVisible ? 'Hide': 'Show'}} Details</button>
        <button @click="toggleFavorite">Toggle to Fav</button>
        <ul v-if="detailsAreVisible">
            <li><strong>Phone: </strong>{{ phoneNumber}}</li>
            <li><strong>Email: </strong>{{ emailAddress}}</li>
        </ul>
    </li>


    
</template>

<script>
export default {
  // props should have same name as data props
  // props:[ 'fullName', 'phoneNumber', 'emailAddress','isFavorite' ],
  props:{
    id: {
      type: String,
      required: true
    },
    fullName: {
      type: String,
      required: true
    },
    phoneNumber:{
     type: String,
     required: true
    },
    emailAddress:{
      type:String,
      required: true
    },
    isFavorite:{
      type:Boolean,
      required: false,
      default:false
    } 
  },
  emits:['toggle-favorite'],
  // emits:{
  //   'toggle-favorite':function(id){
  //     if(id) {
  //     return true;
  //     } else {        
  //       console.warn('id missing');
  //       return false;
  //     }
  //   }
  // },
  data() {
    return {
      detailsAreVisible:false,
      friend: {
          // id: "Gordis",
          // name: "Sam",
          // lastname: "Biden",
          // phone:"281 289 5565",
          // email: "sam@hotmail.com",
          
      },
        //we are doing this to avoid mutation and friendIsFavorite is takien as isFavorite initial value
        //we are using emit so we dont need this anymore
      // friendIsFavorite:this.isFavorite,       
    };
  },
  methods:{
      toggleDetails(){
          this.detailsAreVisible = !this.detailsAreVisible;  
        },
        toggleFavorite(){
          // built method you can call from inside a vue component, emit your own custom event to listen in the parent component, kebak case
          this.$emit('toggle-favorite',this.id);
        }
  }
}  
  </script>