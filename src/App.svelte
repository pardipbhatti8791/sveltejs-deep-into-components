<script>
	import {tick} from 'svelte'
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
	let text ='helly this is dummy text'

	function addToCart(e) {
		console.log(e.detail)
	}

	function transform(e) {
		console.log(e.whcih)
		if(e.whcih !== 9) {
			return ;
		}
		e.preventDefault();
		const selectionStart = e.target.selectionStart
		const selectionEnd = e.target.selectionEnd
		const value = e.target.value

		text = value.slice(0, selectionStart) + 
							value.slice(selectionStart, selectionEnd).toUpperCase() 
							+ value.slice(selectionEnd)
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

<textarea rows="5" value="{text}" on:keydown="{transform}"></textarea>