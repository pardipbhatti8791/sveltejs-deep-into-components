<script>
	import Product from './Product.svelte'
	import Modal from './Modal.svelte'
	
	let showModal = false
	let closeable = false
	let products = [
		{
			id: 'p1',
			title: 'Apple Ipad',
			price: 1000
		}
	]

	function addToCart(e) {
		console.log(e.detail)
	}
</script>

{#each products as product}
<Product 
	{...product}
	on:add-to-cart="{addToCart}"
	on:delete="{(e) => console.log(e.detail)}"
/>
{/each}
<button on:click={() => showModal = true}>Show Modal</button>

{#if showModal}
<Modal content="Hello Gugu" on:close-modal="{() => showModal = false}" let:didAgree={closeable}>
	<h1 slot="header">Hello</h1>
	<p>This is modal</p>
	<button slot="footer" on:click="{() => showModal = false}" disabled={!closeable}>Confirm</button>
</Modal>
{/if}