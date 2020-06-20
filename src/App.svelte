<script>
	import Product from './Product.svelte'

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
	title={product.title} 
	price={product.price}
	on:add-to-cart="{addToCart}"
	on:delete="{(e) => console.log(e.detail)}"
/>
{/each}