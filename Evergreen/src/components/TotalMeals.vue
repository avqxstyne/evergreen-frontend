<script lang="ts">

export default {
        data (){
        },
        methods : {

        // This function retrieves the total number of meals in the database
        getTotal() {
            try {
              
                // Send request to get every meal in the database
                fetch("http://localhost:8080/files/getAll", {
                    method: "GET",
                    headers: {
                    "Accept": "application/json",
                    "Content-Type": "application/json",
                    }
                // Turn request to json data
                }).then(res => {
                    return res.json()

                // Set count equal to the length of the json data, which is the total number of meals
                }).then(data => {
                    let total = (<HTMLInputElement>document.getElementById("num"));
                    total.innerText = data.length;
                })
            } catch(e) {
                console.log(e)
                console.log("AAAAAAA")
            }
          }
        },

        // Set the count variable before page display
        beforeMount() {
            this.getTotal();
        }  
}
</script>

<!-- UI Template -->
<template> 
  <div id="totalmeals">
    <p>Total meals tracked</p>
    <div id="num"> </div>
  </div>
</template>

<!-- Styles -->
<style scoped>
    #totalmeals {
        background-color: rgb(33, 47, 33);
        padding: 1rem;
        margin-bottom: 2rem;
        display: flex;
        flex-direction: column;
        border-radius: 1rem;
        width: fit-content;
        gap: 1rem;
    }

    #totalmeals p {
        font-size: 1rem;
        color: white;
    }

    #totalmeals div {
        text-align: center;
        font-size: 2rem;
        color: rgb(9, 193, 9);
    }
</style>