<script>
import {readable, writable} from "svelte/store";

export const products = readable([
		{id: 1, name: "Apple", image: "https://www.applesfromny.com/wp-content/uploads/2020/05/Jonagold_NYAS-Apples2.png", price: 10, quantity: 1},
		{id: 2, name: "Orange", image: "https://5.imimg.com/data5/VN/YP/MY-33296037/orange-600x600-500x500.jpg", price: 11, quantity: 1},
		{id: 3, name: "Grapes", image: "https://www.aicr.org/wp-content/uploads/2020/01/shutterstock_533487490-640x462.jpg", price: 12, quantity: 1},
	])
export const cart = writable([])

	
	const minusItem = (product) => {
		for(let item of $cart) {
				if(item.id === product.id) {
					if(product.quantity > 1 ) {
							product.quantity -= 1
							$cart = $cart
					} else {
							$cart = $cart.filter((cartItem) => cartItem != product)
					}
					return;
				}
		}
	}
	
	const plusItem = (product) => {
			for(let item of $cart) {
							if(item.id === product.id) {
								product.quantity += 1
								$cart = $cart;
								return;
							}
					}
	}

		$: total = $cart.reduce((sum, item) => sum + item.price * item.quantity, 0)
	
</script>

<div class="cart-list">
	{#each $cart as item }
		{#if item.quantity > 0}
		<div class="cart-item">
			<img width="50" src={item.image} alt={item.name}/>
			<div>{item.quantity}
				<button on:click={() => plusItem(item)}>+</button>
				<button on:click={() => minusItem(item)}>-</button>
			</div>
			<p>₹{item.price * item.quantity}</p>
		</div>
		{/if}
	{/each}
	<div class="total">
		<h4>Total: ₹ {total}</h4>
	</div>
</div>


<style>
	.cart-item {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
	}
	
	.total {
		text-align: right;
	}
	
	.cart-list {
		border: 2px solid;
		padding: 10px;
	}
</style>