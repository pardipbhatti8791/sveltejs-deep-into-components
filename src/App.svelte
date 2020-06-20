<script>
	import Product from './Product.svelte'
</script>

<Product 
	productTitle="Meri Gugu" 
	on:add-to-cart="{(e) => console.log(e)}"
	on:delete="{() => alert('deleted')}"
/>