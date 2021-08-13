<template >
<the-header title="Learning Resources">

</the-header>
<stored-resources :resources="storedResources">

</stored-resources>
</template>

<script>
import StoredResources from  "./components/learning-resources/StoredResources.vue"
import TheHeader from "./components/Layouts/TheHeader.vue"
export default {
components:{
    StoredResources,TheHeader

},
    data(){

return{
    storedResources:[{

        id:"official guide",
        title:"official guide",
        description:"official guide",
        link:"https://www.google.com/"
    },
    
    {

        id:"Home guide",
        title:"official guide",
        description:"official guide",
        link:"https://www.google.com/"
    }]
}

    }
  
}
</script>

 <style >
 @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}

 </style>