<script>
	import Product from './Product.svelte'

	function addToCart(e) {
		console.log(e.detail)
	}
</script>

<Product 
	productTitle="Meri Gugu" 
	on:add-to-cart="{addToCart}"
	on:delete="{(e) => console.log(e.detail)}"
/>