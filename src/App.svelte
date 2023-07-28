<script>
  import Modal from './modal.svelte'
  import Form from './form.svelte';

let people=[
  
	{name:'sharon', color:'red',age:12,id:1},
	{name:'babu',color:'blue',age:13,id:2},
	{name:'john',color:'green',age:45,id:3}
];

const handleClick=(id)=>{
	//deleting persons
	
	people=people.filter((person) => person.id != id)

}

const addPerson=(event)=>{
const person=event.detail
people=[person,...people]
showModal=false;


}

let showModal=true;

const toggleModal=()=>{
	showModal=!showModal
}




// let num =40;
</script>

<!-- {#if num>100}
<p>num greater than 100</p>
{:else if num==10}
<p>num is equal to 10</p>
{:else}
<p>number less than 100 </p>
{/if} -->



<Modal message="hello world" ispromo={true}	showModal={showModal}  on:click={toggleModal}>
	<h3>Add New Person</h3>
	<Form on:addPerson={addPerson}/>
</Modal>



<main>
	<button on:click={toggleModal}> open Modal</button>
{#each people as person}
<div >
	<h3>{person.name}</h3>
	{#if person.color=='red'}
	<p style="color: {person.color};">Ninja</p>
	{/if}
	<h4>wears a {person.color} belt and is of age {person.age}</h4>
	<button on:click={()=>{handleClick(person.id)}}>Delete</button>
	

</div>
{:else}
<p>there are no results to show...</p>
{/each}
	
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}



	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>