<script>
export let message; 
export let showModal=false;
export let ispromo=false;

</script>


{#if showModal}
<div class="backdrop" on:click|self >
    <div class="modal" class:promo={ispromo} >
        <slot></slot>
    </div>
</div>
{/if}




<style>
.backdrop{
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgb(72, 68, 68);
}

.modal{
    max-width: 400px;
    margin: 10% auto;
    padding: 10px;
    border-radius: 10px;
    text-align: center;
    background-color: white;
}
.promo.modal{
    background-color: crimson;
    color: white;
}
</style>