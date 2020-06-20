<script>
	import Product from './Product.svelte'
	import Modal from './Modal.svelte'
	

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

<Modal content="Hello Gugu">
	<h1 slot="header">Hello</h1>
	<p>This is modal</p>
	<button slot="footer">Confirm</button>
</Modal>