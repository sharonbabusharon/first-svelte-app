<script>

import {createEventDispatcher} from 'svelte';

let dispatch =createEventDispatcher()

let name='';
let color='';
let age='';
let skill=[];



const handleForm=()=>{
   const person={
    name:name,
    color:color,
    age:age,
    skill:skill,
    id:Math.random()
   };
   dispatch('addPerson',person)
}

</script>


<main>
    <form on:submit|preventDefault={handleForm}  >
        <input type="text" placeholder="name" bind:value={name}>
        <input type="number" placeholder="age" bind:value={age}>
        <label>Skills:</label>
        <!-- <input type="checkbox" bind:checked={Fighting} >Fighting<br>
        <input type="checkbox" bind:checked={Sneaking} >Sneaking<br>
        <input type="checkbox" bind:checked={Running}>Running<br> -->
        <input type="checkbox" bind:group={skill} value="Fighting">Fighting<br>
        <input type="checkbox" bind:group={skill} value="Sneaking">Sneaking<br>
        <input type="checkbox" bind:group={skill} value="Running">Running<br>
        <label>Belt Color<label>
            <select bind:value={color}>
            <option value="black">black</option>
            <option value="green">green</option>
            <option value="blue">blue</option>
            <option value="orange">orange</option>
        </select>
        <button>add Person</button>
    </form>

</main>

<style>


</style>