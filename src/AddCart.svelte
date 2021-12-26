<script>

     let products = [
  {id: 1, name: "Apple", image: "/path/to/apple.png", price: 10, quantity: 1},
  {id: 2, name: "Orange", image: "/path/to/apple.png", price: 11, quantity: 1},
  {id: 3, name: "Grapes", image: "/path/to/apple.png", price: 12, quantity: 1, componet: Product},
]

 let cart = [];


  const addToCart = (product) => {
  for(let item of cart) {
    if(item.id === product.id) {
	product.quantity += 1
	cart = cart;
	return;
     }
   }
  cart = [...cart, product]
}
  $: total = cart.reduce((sum,item) => sum + item.price * item.quantity, 0)
</script>

<div class="cart-list">

 {#each cart as item }
   <div class="cart-item">

     <img width="50" src={item.image} alt={item.name}/>
     <div>{item.quantity}</div>
     <p>${item.price * item.quantity}</p>
   </div>
 {/each}
 </div>
<div class="product-list">
 {#each products as product}
   <div>
    <div class="image" style="background-image: url({product.image})"></div>
    <h4>{product.name}</h4>
    <p>₹{product.price}</p>
    <button on:click={() => addToCart(product)}>Add to cart</button>   </div>

 {/each}
</div>
             <h1 class="total">Total {total}</h1>

<style>
    .total{
        text-align:text;
    }
 .product-list {
   display: grid;
   grid-template-columns: repeat(3, 1fr);
 }
</style>