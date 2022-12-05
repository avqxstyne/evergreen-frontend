<script lang="ts">

export default {
        data (){
            return {
              
            }
        },
        methods : {
          entry(e: Event) {
            e.preventDefault();
            let date: String = (<HTMLInputElement>document.getElementById("i1"))?.value.toString();
            let name: String = (<HTMLInputElement>document.getElementById("i2"))?.value.toString();
            let calories = Number((<HTMLInputElement>document.getElementById("i3"))?.value);
            let fat = Number((<HTMLInputElement>document.getElementById("i4"))?.value);
            let protein = Number((<HTMLInputElement>document.getElementById("i5"))?.value);
            let carbs = Number((<HTMLInputElement>document.getElementById("i6"))?.value);

            console.log(date);
            console.log(name)
            console.log(calories)
            console.log(fat);
            console.log(protein)
            console.log(carbs)

            try {
              
            fetch("http://localhost:8080/files/add", {
              method: "POST",
              headers: {
                "Accept": "application/json",
                "Content-Type": "application/json",
              },
              body: JSON.stringify({
                "name": name,
                "date": date,
                "calories": calories,
                "fat": fat,
                "protein": protein,
                "carbs": carbs
              })
            }).then(res => {
              console.log(res)
            })
            } catch(e) {
              console.log(e)
              console.log("AAAAAAA")
            }
          }
        }
    }



</script>

<template>
  <form id="balls">
    <h1 id="evergreen-header">Add new meal</h1>

    <div id="input-flexbox">
        <input
          placeholder="mm/dd/yyyy"
          id="i1"
        >
        <input
          placeholder="Meal Name"
          id="i2"
        >
        <input
          placeholder="Calories"
          id="i3"  
        >
        <input
          placeholder="Fat"
          id="i4"
        >
        <input
          placeholder="Protein"       
          id="i5"  
        >
        <input
          placeholder="Carbs"
          id="i6"
        >
    </div>
    <button type="submit" id="balls-button" v-on:click="entry($event)">Submit meal entry</button>
  </form>

 
</template>

<style>

#balls {
  background-color: rgb(33, 47, 33);
  width: 50%;
  padding: 2rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  border-radius: 1rem;

}
#balls-button {
  background-color: green;
  border-radius: 9999px;
  color: white;
  outline: none;
  border: none;
  margin-block: 1rem;
  max-width: fit-content;
  padding-inline: 2.25rem;
  padding-block: 0.5rem;
}

#evergreen-header {
  font-size: 3rem;
  color: var(--vt-c-white-soft);
}

#input-flexbox {
  display: flex;
  align-items: center;
  justify-content: left;
  gap: 1rem;
  flex-wrap: wrap;
}

#input-flexbox input {
  background-color: transparent;
  border: 0;

  border-bottom: 4px solid green;
  box-shadow: none;
  color: white;
  appearance: none;
  font-size: 1rem;
  padding-inline: 1rem;
  padding-block: 0.5rem;
  transition: 1s;
}

#input-flexbox input:focus {
  border: none;
  border-bottom: 4px solid rgb(0, 128, 126);

  outline: none;
}




</style>
